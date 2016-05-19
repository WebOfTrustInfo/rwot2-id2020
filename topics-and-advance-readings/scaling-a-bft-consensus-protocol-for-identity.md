Scaling a BFT Consensus Protocol for Identity
========
Jason Law & Lovesh Harchandani

18 May 2016

Submission for the ID2020 Design Workshop

# Introduction

Byzantine Fault-Tolerant protocols are traditionally not very scalable. In fact, last year when I first approached Dr. Pierre Louis Aublin, one of the authors of the RBFT paper on which the Plenum protocol is based, and I asked his thoughts about scaling a BFT protocol, he started to laugh. 

BFT protocols are hard to scale.

In contrast to traditional enterprise distributed systems, adding more nodes does not improve the throughput. In fact, adding nodes, while increasing the integrity of the system, actually reduces its overall throughput.

In this paper, we will briefly describe Plenum, the consensus protocol used for the Sovrin Distributed Identity Ledger. Then we’ll discuss a set of mechanisms that allow us to scale it.

# Background and Framing

## Byzantine Fault-Tolerant Protocols

The Byzantine generals problem was first introduced in a paper of the same name by Lamport, Shostak, Pease in 1982. However, crash fault-tolerant protocols like Paxos are not equipped to deal with compromised (malicious) nodes. In 1999, Miguel Castro and Barbara Liskov introduced the venerable "Practical Byzantine Fault Tolerance" (PBFT) algorithm, which has become the starting point for many investigations in this space. However, PBFT has several limitations.

First, as described in the Aardvark paper (Clement et al., Making Byzantine fault tolerant systems tolerate Byzantine faults, NSDI '09), a malicious client can trigger view changes at will that will stop the progression of the protocol. Second, from an implementation point of view it does not separate the logic of accepting client requests and ordering them, which leads to possible DoS attacks from the client. Third, a malicious primary can order requests at an arbitrary speed without being detected. These problems are fixed in Aardvark. 

RBFT improves Aardvark by executing several protocol instances with different primaries in parallel to detect any performance problem in real-time, without assuming anything about the previous or future performance/condition of the system. Aardvark raises the expected throughput expectation based on the past and triggers a view change as soon as the primary fails to match those expectations. This is fine when the load is static. But fails to detect a poor performing primary when load is not near the peak. RBFT resolves this.

## Plenum

Plenum extends RBFT in several ways.

1. Plenum uses digital signatures for inter-node communication, whereas RBFT uses MAC authenticators. MAC authenticators are faster, but digital signatures supply non-repudiation.

2. In Plenum, the client is not required to send requests to all the nodes like in RBFT but only to *f+1* nodes, *f* being the number of faulty nodes.

3. RBFT leaves the Primary election process up to implementation, Plenum provides 2 Primary election mechanisms, one deterministic and one non-deterministic.

4. In RBFT each replica is required to communicate its 3PC message to other replicas in a point-to-point fashion whereas in Plenum replicas can gossip their received 3 phase messages which allows Plenum to progress faster in partially partitioned networks.

5. RBFT leaves the implementation details of blacklisting clients and node on the implementation whereas Plenum defines multiple blacklisting strategies. Plenum considers the severity of the fault and applies the appropriate blacklisting strategy.

6. Plenum adds a mechanism for crashed/recovered nodes or new nodes to efficiently and securely catch up.

## Throughput requirements of an identity ledger

Assumptions about the number of transactions for a global scale identity system can vary widely. For example, we could take the stance that we simply store identifiers (double-spend-proof) and some hashes for attributes/credentials/claims which are stored off-chain. Attribute exchange and all interactions happen off-chain. In this case, the number of transactions that would need to be supported would be minimal, even for very large populations.

Another set of assumptions could see us storing encrypted attributes in a ledger. What if authentication attempts and their results were stored in the ledger? It could be argued that your identity is ultimately best defined by your reputation ([https://openreputation.net/open-reputation-low-level-whitepaper.pdf](https://openreputation.net/open-reputation-low-level-whitepaper.pdf)). If added to a ledger, reputation events could result in a very high number of transactions.

Some privacy-preserving protocols can be particularly heavy. For example, take the case where I have access to certain benefits because I’m an employee of XYZ Corp. XYZ Corp provides a credential, but they need to be able to revoke it. For example, at the time of issuance, they won’t know *when *I might be fired for cause. Revocation of that credential could be stored in a distributed ledger. But, in order to avoid unwanted correlation, XYZ Corp could publish a number of anonymous commitments, and I could provide a non-interactive zero knowledge proof for set membership ([https://infoscience.epfl.ch/record/128718/files/CCS08.pdf](https://infoscience.epfl.ch/record/128718/files/CCS08.pdf)), in this case, the set of employees of XYZ Corp. This scheme would require a periodic (perhaps daily) update of those commitments, which, for a large organization, would be quite intensive.

It is hard to predict how a system will ultimately be used, so it is safest to base assumptions on the worst case scenarios.

## Geography

A sovereign identity ledger intended to operate at global scale needs validator nodes spread around the globe. This is the best insurance against undue influence from any single legal jurisdiction. It must also survive natural disasters. This physical distance means latency between nodes can vary greatly. The fastest an electromagnetic signal can travel around the earth is roughly 130 ms. Add in slower media and internet routers and you are looking at 200 to 300 ms for a round trip. Factor in the "chatty" nature of BFT protocols and suddenly those milliseconds start to add up.

## Double-Spend-Proof

Not all transactions need to be double-spend-proof. For example, adding a unique identifier needs to be double-spend-proof. I don’t want to register a unique identifier only to find that someone else has the same unique identifier. However other transactions, such as adding an attribute to that unique identifier, may not need to be double-spend-proof. This allows for flexibility in allocating validators for particular transactions. Not all validators need to participate in every transaction.

## Governance

A sovereign identity system needs to be trusted. If that system is a permissioned distributed ledger, then it needs world-class governance. Some basic requirements for this include:

1. As light as possible but no lighter.

2. Trustees dispersed across multiple geographies, industries, domains.

3. Formation of a small number of committed working groups.

4. Stewards selected based on meeting a core set of requirements and ledger-based voting

5. Push as much to the algorithms as possible

    1. A dedicated ledger for consensus pool membership

    2. Probationary period for new validators

    3. Performance metrics published to the ledger, with Tattling protocol

    4. Blacklisting, time-out, three-strikes, and ledger-based appeal

    5. Observer nodes serve as hot-standby nodes

# How to Scale It

As a BFT consensus pool grows, the number of faulty nodes it can tolerate grows. Adding nodes incurs greater networking and CPU costs. At a certain point, the marginal utility of being able to tolerate an additional faulty node is vanishingly small. Thus there is a sweet spot for the size of the consensus pool that balances cost with system integrity. 

The following is an initial proposal for how to scale a consensus protocol that is widely considered difficult to scale. 

## Pools

Validators can be broken up into pools. Pools would grow deterministically as nodes are added. Pools would maintain diversity of administration. New pools would be formed according to thresholds based on the optimum pool size. Validation in the pool would happen against the replicated master ledger plus any local (pool) transactions not yet applied to the master. Periodically, the pools would post their local transactions to those validators designated as Supernodes. Supernodes could ultimately be responsible for committing those validated transactions to the master ledger.

## Key Segregation

If independent pools will be validating transactions, then those transactions will either need to be double-spend-proof, or the protocol will need to allow for pool-validated transactions to be rejected at the Supernode level. Though this is possible, it is not ideal because it defeats one benefit of BFT protocols: fast commits. If the Supernodes can invalidate a previously validated transaction, then a transaction that takes less than one second to be committed could now take five seconds.

One way to solve this is key segregation, i.e., having the protocol deterministically allocate identifiers to a pool. If the number of pools is 5, then a hash of an identifier mod 5 could tell us which pool to use to validate transactions for that identifier. This could be: a) determined by the client; b) part of the validation rules of a pool, and c) double-checked quickly by the Supernodes. It is essentially load balancing a BFT protocol.

The protocol would need to handle the case when a pool is added or removed. This should be relatively simple since it does not matter which pool validates a transaction, just as long as it the transaction is validated and added to the ledger.

Of course, this makes an assumption about how transactions are structured. There may be some types of transactions that need to be validated against the master ledger, not just against the master ledger plus locally validated transactions. This might require treating Plenum as a closed-loop protocol. Since it is currently an open-loop consensus protocol, this might require that the caller wait for validation of one transaction before submitting subsequent transactions.

## Multiple Discrete Ledgers

A BFT consensus protocol, as a mechanism for replicating state machines, allows for multiple independent or semi-dependent ledgers. For example, Plenum actually maintains a different ledger for pool membership, i.e., who can be a Validator. In the same way, each of the pools described above could maintain its own ledger. Validation of incoming transactions can be performed across these multiple ledgers. The "master ledger" mentioned above could be a logical ledger, with the physical implementation being a collection of these separate ledgers. Alternately, these ledgers could be checkpointed against each other as an alternative to having one master ledger.

## Backpressure

Supernodes could signal to pools how often to push local transactions. The frequency of local transaction submissions could be fairly high, e.g., once per second. But if the Supernodes had trouble keeping up with the frequency of submissions, they could signal submitting nodes to batch more local transactions and submit them less frequently, establishing a tradeoff between throughput and latency.

## Ensuring Diversity of Administration

By giving nodes attributes for administrative and jurisdictional domains, a governance algorithm can enforce diversity within a pool. For example, if an organization was allowed to have more than one Validator node, the algorithm could restrict those validators from being in the same sub-pool at the same time. A governance rule could also limit the potential influence of any one legal jurisdiction. For example, no sub-pool could have more than 5% of its nodes residing in any one country.

## Mitigating Some Attack Vectors

To reduce the risk of a critical mass of nodes in a pool being compromised, pool membership could change dynamically. Because at least ⌊(n+2)/3⌋ nodes need to be compromised to stop a pool, at least 7 nodes  would need to be compromised in a pool of 19. Assuming an attacker could successfully compromise that many nodes, dynamically changing pool membership would make it vastly harder since now those 7 nodes would periodically be assigned to different pools.

Based on the entropy provided from the current merkle root hash, nodes could independently propose a switch with another node—essentially swapping places. The request to switch places can be justified by an algorithm based on the hash of the shared ledger along with other factors such as how long each node has been in its respective pool. If a node refused to switch places, it would be clearly visible and the node could be flagged as suspicious. Inappropriate requests to switch places would also be clearly visible.

## "Understudies"

In Sovrin, not all nodes are Validators. In a permissioned model, there will need to be some mechanism for allowing new Stewards (those entities responsible for administering a node), and new Validators. One way to do that is to allow new candidate Stewards to stand up nodes that act as understudies, They will serve for a time in this capacity, paying their dues so to speak, and establishing themselves to some degree. When the algorithm requirements are met, they are called up to be full Validators.

### Reads vs. Writes

Understudies can serve as read-only nodes. Because Writes are expensive computationally and network-wise, offloading reads from the Validators will free them up to be able to focus on writes. These Understudies can effectively be the Content Delivery Network for the distributed ledger, moving reliable copies of the data closer to consumers of that data. In fact, an organization might want to host an Understudy just to have very fast local lookups against the ledger. Of course clients could host a full copy of the ledger, but with strong consistency and inclusion proofs against the merkle tree, clients having full copies of the ledger may not be necessary.

### Hot-Spares

BFT protocols typically follow the rule that the number of nodes needed to tolerate f faulty nodes is 3f+1. Once a node is compromised, if it behaves inappropriately it is blacklisted. There are provisions in the governance that allow for a Validator’s Steward to respond to a blacklisting with an assertion that the problem is rectified, which would allow it to be trusted again. But if a node is blacklisted, or is simply down for a period of time, this consumes one of the slots for allowed faulty nodes.

A way to mitigate this is to employ Understudy nodes as hot-standbys like with a RAID system. Because Validator pool membership is managed with a ledger, the nodes themselves could independently recognize a missing member, and propose the admission of the highest-ranking Understudy, assuming it meets the diversity of administration requirements. Through consensus, the other nodes would agree to the change.

## A Cluster of Hosts as a Logical Node

A node can be abstracted so it can be run as one physical machine *or* as a cluster of several physical machines. So we could define a node as a collection of servers, where the different components (monitoring, dispatch, propagation, validation, replicas, etc.) are dispersed among the servers. The throughput of the system as a whole would increase as more of these clusters came up. Of course, if a node is deemed malicious, the collection of servers constituting that node is considered malicious. That node still gets only one vote no matter how powerful it is.

# In Conclusion

Some of the mechanisms discussed above are in place and working in Plenum and Sovrin today. Others will be implemented as real-world observations dictate. There are a myriad of optimization opportunities, and the use cases will drive which will happen, and when.

We welcome the discussion.
