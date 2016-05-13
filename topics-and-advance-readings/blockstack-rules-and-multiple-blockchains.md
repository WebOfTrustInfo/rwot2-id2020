## Blockstack Rules and Support for Multiple Blockchains

We've already submitted the [blockstack paper](https://blockstack.org/blockstack.pdf) (to be published at [USENIX ATC'16](https://www.usenix.org/conference/atc16))
as advanced reading for the workshop.

Greg recently started a discussion about decentralization properties of Blockstack. We really appreciate that he took the time to 
start this discussion, because we believe that it's very important that decentralization properties are well understood and any concerns about
centralization are properly addressed.

In this document, I'm going to go over Greg's points and provide some additional information that is not in the Blockstack paper draft yet. Readers are encouraged to read Greg's [full document](https://github.com/WebOfTrustInfo/ID2020DesignWorkshop/blob/master/topics-and-advance-readings/no-secure-protocol-equals-no-sovereign-identity.md) for proper context.

**Issue #1: Who has control over protocol rules**

Blockstack has a set of "valid rules" that are written in each version of the software and transcations not complying to those rules
are rejected by the nodes. These protocol rules are similar, in a way, to Bitcoin protocol rules. You can create a different version of
Bitcoin by tweaking some protocol rule. People do this all the time e.g., Litecoin changed target block processing time to 2.5 minutes
instead of 10 minutes. By making changes to protocol rules you essentially create a fork of the network/blockchain and are now on a 
seprate network which is not compatible with Bitcoin. 

Here is the direct quote from Greg:
> Blockstack's protocol does not seem to be completely decentralized, as Blockstack appears to have complete control when it comes to making changes to it.

His concern is about (a) who has control over defining protocol rules, and (b) when/if can they change and who can change the rules. This is a completely fair concern.
The current software developers for [blockstack-server](https://github.com/blockstack/blockstack-server) and the original protocol designers of Blockstack wrote the first rule set of protocol rules (similar to how Satoshi Nakamoto designed 
the Bitcoin protocol and wrote the first implementation). Moving forward, a
non-profit foundation (the Blockstack Foundation) with multiple companies and open-source developers as members will have control over the
protocol rules for a reference implementation. What's important to remember is that:

a) The software is open-source and no one can force you to upgrade to any specific version e.g., if any new rules are introduced that you don't like. You
can keep running an old version of the software and ask your friends and people you want to collaborate with to use the version that you're using as well.
This is similar to Bitcoin developers trying to introduce some controversial change and miners/full-nodes refusing to upgrade their software. So ultimately
it's the people who're in control, not even the non-profit foundation can force a new version on you. 

b) You can, at any point, fork the code and change the rules to start a new network. This is similar to how people fork Bitcoin and start
alt-coins. Another analogy is IRC chat channels. Versions of blockstack-server that have the same rules are like an IRC channel. Everyone can see/find
each other and have the same view of the network. You can start a different IRC network/channel and invite your friends to it. No one can stop you from doing that.
Eventually, people would go to the IRC universe where all their friends are i.e., people will run the version
of blockstack-server that has the most number of users or where all their friends are.

This model is fully decentralized because there is no single party that can change/modify the rules for everyone else. People can choose 
what "identity universe" they want to be a part of and what fork/version of the software they want to use. 

**Issue #2: Blockstack is tied to Bitcoin**

In the [Blockstack paper](https://blockstack.org/blockstack.pdf), we discuss how as a design principle Blockstack is agnostic of the underlying blockchain. Currently, it uses the Bitcoin
blockchain because it's currently the most secure blockchain, but the system can migrate to other blockchains as well. In fact, Blockstack
has been running in production for 2+ years and is the only system (that I am aware of) that has successfully completed a migration of
a production system from one blockchain (Namecoin) to another blockchain (Bitcoin). 

Here is the direct quote from Greg about dependency on Bitcoin:
> Blockstack's protocol appears entirely focused on the workings of a single implementation of the general concept of a blockchain (Bitcoin).

> This specific implementation (Bitcoin), could at any point fail to serve as a long-lived host platform for SSI for a large variety of reasons. Similarly, the specific implementation of Blockstack could also fail.

In case Bitcoin fails, it will trigger a migration event to another blockchain. Blockstack has full support for this already i.e., the code
and migration system is already in place. So risk of Blockstack failing is completely decoupled from the failure of the underlying blockchain. 

Secondly, there is work under progress where Blockstack will support multiple blockchains. Here is a slide from a recent presentaiton I gave:

![Image of multiple blockchains on Blockstack](http://muneebali.com/static/files/multiple_blockchains.png)

This work is under progress and more details will come out, but the basic idea is that Blockstack will store information about the TLDs/namespaces
on a single blockchain. This can be any blockchain, the only requirement is the security level/guarantees of the blockchain. Individual namespaces/TLDs like .id
will specify the blockchain on which that namespace information is available e.g., .id can point to Bitcoin and .eth can point to Ethereum. We're already
working with people from Ethereum and some other larger corporations to push this work forward. This further reduces any dependency on Bitcoin.

To summarize, Blockstack is designed to survive a failure of any underlying blockchain i.e., a failure of Bitcoin will not result in a failure of Blockstack, and there is already work in progress to support multiple blockchains.

P.S: Check out the [virtualchain library](https://github.com/blockstack/blockstack-virtualchain) that is used to write drivers for other blockchains. We can use help from the community to write drivers 
for other blockchains!
