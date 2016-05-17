# Decentralized Identifiers (DIDs) and Decentralized Identity Management (DIDM)

A paper for the ID2020 Design Shop
Les Chasen, Respect Network
2016-05-16

In recent years, data technologies have emerged with the potential to differentiate and protect identity in ways that are similar, but superior, to those used in the physical world for millennia.  Identity in the physical world has typically been asserted via decentralized mechanisms, mainly paper; i.e., identity is managed individually with claims and attributes that are verified by third parties. Modern computing techniques have centralized this process with various registries and databases that have become repositories for unintentional exploitation. New decentralized technologies, such as blockchains, hash tables and semantic data graphs can enable the design and deployment of a decentralized identity architecture that can vastly improve security and privacy of individuals and entities in the digital world.  This will lead to users on the internet becoming individuals with sovereign rights and ownership and control over their digital selves in similar ways that we have control over our physical selves.

Blockchain and distributed ledger technologies provide a decentralized foundation for privacy-respecting identity management infrastructure. Decentralized Identifiers (DID) stored in a permissioned blockchain enable principals to directly control their own identities with cryptographic proofs and secure, addressable network endpoints.

DIDs further enable a Decentralized Identity Management (DIDM) infrastructure that will empower people and organizations to securely and confidentially manage and assert their identities. Open standards and established industry protocols will permit principals to selectively disclose identity claims and to manage their privacy and digital relationships.

What might an Internet wide fabric look like for DIDs and DIDM? Such an architecture, using public and/or private blockchains as "identity backbones", need to meet traditional information security principles such as confidentiality, integrity, availability, non-repudiation and provenance.  Further, privacy-by-design principles apply, including user control, selective disclosure of information and pseudonymity.

There have been several recent related efforts to start to explore Decentralized Identity. For example:

### **W3C Credentials Community Group**

Started in December 2014 by Manu Sporny and Dave Longley of [Digital Bazaar](http://digitalbazaar.com/), the goal of this group is stated on [their home page](https://www.w3.org/community/credentials/):

The goal of this Group is to forge a path for a secure, decentralized system of credentials that would empower both individual people and organizations on the Web to store, transmit, and receive digitally verifiable proof of qualifications and achievements.

The W3C Credentials Community group is an offshoot of the [Web Payments Community Group](https://www.w3.org/community/webpayments/), which also has decentralization as a key goal. From their charter:

The goal is to create a safe, decentralized system and a set of open, patent and royalty-free specifications that allow people on the Web to send each other money as easily as they exchange instant messages and e-mail today. 

Both of these W3C Community groups have identified *decentralized identifier registration and resolution* as a key infrastructure capability they need to achieve their objectives—so much so that the Credentials Community Group created a separate draft specification called [A Decentralized Hashtable for the Web](http://opencreds.org/specs/source/webdht/) that is focused entirely on this problem. From the Introduction:

The Web currently does not have a mechanism where people and organizations can claim identifiers that they have sole ownership over. Identifiers, such as those rooted in domain names like emails addresses and website addresses, are effectively rented by people and organizations rather than owned. Therefore, their use as long-term identifiers is dependent upon parameters outside of their control. One danger is that if the rent is not paid, all data associated with the identifier can be made temporarily or permanently inaccessible.

### **XDI.org Registry Working Group (XRWG)**

[XDI.org](http://xdi.org/) is an international non-profit organization founded to advance the development and adoption of the [XDI (Extensible Data Interchange)](https://www.oasis-open.org/committees/xdi/) protocol, an emerging standard for semantic data interchange from the [OASIS XDI Technical Committee](https://www.oasis-open.org/committees/xdi/).

In April 2015 the XDI.org trustees formed the XDI Registry Working Group (XRWG) to transition XDI registry infrastructure from a centralized model to a new decentralized blockchain-based model. 

The charter of the XRWG includes [the following principles](https://docs.google.com/document/d/1i-XChGFsuAi-Id85FWXjX6hOWDn9Sq-qe7ARykJgsBI/edit#heading=h.ijm5zrz1xq4t):

**Maximum interoperability.** The XDI Registry must conform to the OASIS XDI open standard for semantic data interchange and should enable any set of XDI users and communities to discover and interoperate with each other.

**Minimum viable centralization.** The XDI Registry should be designed to be as decentralized as possible.

**Critical infrastructure.** The XDI Registry must provide for a high level of reliability, stability, scalability, security, sustainability and other requirements typical of critical internet infrastructure.

**Sovereign identity.** The XDI Registry should enable any XDI authority (person or organization) to fully administer its own registry and/or its own entry in an xdi.org-specified registry, without the need to rely on any particular external administrative authority.

**Neutrality.** The XDI Registry should be available to all members of the public and should not discriminate against any party that wishes to use it for any lawful purpose.

### **Rebooting the Web of Trust Group**

This group was formed at the invitation of Christopher Allen, co-author of the SSL 3.0/TLS 1.0 specification. It held its first meeting in San Francisco the first week of November 2015. Inspired by the upcoming 25th anniversary of the original PGP "web of trust", the purpose of the initial meeting of the group is described on [its home page](http://www.weboftrust.info/):

This facilitated design workshop ("DesignShop") is focused on the creation of the next generation of decentralized web-of-trust based identity systems.

The group included three of the top bitcoin core developers (Greg Maxwell, Peter Wuille, and Peter Todd), the founder of [Ethereum](https://www.ethereum.org/) (Vitalik Buterin), the founder of [IPFS](https://ipfs.io/) (Juan Benet), and over 25 other leaders in cryptography, security, privacy, and reputation systems. The group produced five white papers on the topics the participants considered most essential to the establishment of a blockchain-based web of trust. The paper that attracted the highest participation was called [Decentralized Public Key Infrastructure (DPKI)](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/final-documents/rebranding-web-of-trust.pdf). From the abstract:

Today’s Internet places control of online identities into the hands of third-parties. Email addresses, usernames, and website domains are borrowed or "rented" through DNS, X.509, and social networks. This results in severe usability and security challenges Internet-wide. This paper describes a possible alternate approach called decentralized public key infrastructure (DPKI), which returns control of online identities to the entities they belong to. By doing so, DPKI addresses many usability and security challenges that plague traditional public key infrastructure (PKI). DPKI has advantages at each stage of the PKI life cycle. It makes permissionless bootstrapping of online identities possible and provides for the simple creation of stronger SSL certificates.

## **A Decentralized Identifier (DID) Service for Decentralized Identity Management (DIDM)**

A DID system based on blockchain technology (whether public or private; permissioned or permissionless) may be suited for implementing some aspects of classic information security principles, its not well-suited for other aspects. This dichotomy is expressed in [a December 2015 article](https://medium.com/@ConsenSys/tell-me-who-you-are-258268bf3180#.3wi6xq5m9) about blockchain identity by DOD consultant and [Simple Critical Infrastructure Map](http://resiliencemaps.org/) pioneer Vinay Gupta:

Blockchains are great for pointing out things that we want to prove to other people: "look, it is right here, in the blockchain." This is great for things like property registers, but perhaps not quite so great when it comes to all the things we want to selectively disclose.

So what if the architecture is a little different: what goes in the blockchain isn’t the data — or, in many cases, even the hash of the data. Instead, we store a signed statement from a seriously credible source, or the necessary information required for a zero knowledge proof. A thing we might often store would be a public key, or a set of statements-and-signatures on a public key. It might be a script to perform some function, but without tons of personal information on it.

This is a *transactional* vision of the blockchain: something that’s a little less about storing the entirety of our being on a permanent record, but more focussed on disclosing the minimum required for people to be able to do business (or other critical functions) together.

A DID architecture should focus on the set of components that Mr. Gupta refers to as "the minimum required for people to be able to do business (or other critical functions) together".

### **A Decentralized Identifier (DID) Registry and Discovery Service**

This "minimum required" is defined by a union of the proposed requirements identified by the W3C Credential Community Group, the XDI.org Registry Working Group, and the Rebooting the Web of Trust group. It consists of three functions that can be addressed by a combination of blockchain and DHT technology:

1. **A DID registration function** that enables registering a decentralized identifier and its associated metadata (DID document) in the blockchain such that:

    1. The principal (person, group, organization) fully owns and controls the DID and DID document and is not dependent on an intermediary to maintain it.

    2. The registration lasts for the lifetime of the blockchain or DHT.

    3. The DID document contains the cryptographic key material necessary for the registrant to prove ownership and/or control of the DID and DID document.

    4. The DID document contains one or more DIDM service endpoint locators where additional DIDM functions may be accessed.

2. **A discovery function** that enables looking up a registered DID in the blockchain to obtain and validate the integrity of its DID document.

3. **A master key recovery function** that enables the principal to recover control of the DID and DID document in case of loss or compromise of the registrant’s private key.

Together these three functions provide a "bootstrap layer" for a decentralized identity management (DIDM) system. However by themselves, they do not fully address information security and privacy principles. There are gaps:

<table>
  <tr>
    <td>Principle</td>
    <td>Provided by DID</td>
    <td>Gap</td>
  </tr>
  <tr>
    <td>Confidentiality</td>
    <td>A master hierarchical deterministic (HD) public key associated with a principal’s identity can be used to generate child keys to encrypt data and claims</td>
    <td>No HD key management features</td>
  </tr>
  <tr>
    <td>Integrity</td>
    <td>The master HD public key associated with a principal’s identity can be used to validate changes to the DID document </td>
    <td>No HD key management features</td>
  </tr>
  <tr>
    <td>Availability</td>
    <td>Very high availability due to P2P distribution of the blockchain</td>
    <td>Does not cover identity attributes and claims not stored in the blockchain</td>
  </tr>
  <tr>
    <td>Non-repudiation</td>
    <td>Provides non-repudiation of the original DID registration transaction and subsequent changes through proof-of-existence</td>
    <td>Does not bind an identity to attributes that can be used for non-repudiation of actions taken with the principal’s private key(s)</td>
  </tr>
  <tr>
    <td>Provenance</td>
    <td>Static proof-of-existence claims of original DID registration and changes</td>
    <td>Does not address provenance of attributes or claims beyond the DID registration</td>
  </tr>
  <tr>
    <td>Pseudonymity</td>
    <td>Partially addressed by registration of pseudonymous DIDs</td>
    <td>Does not address management of pseudonymous DIDs</td>
  </tr>
  <tr>
    <td>Selective disclosure</td>
    <td>Partially supports selective disclosure through the use of one-time child keys to prevent correlation</td>
    <td>Does not address selective disclosure of private attributes, claims, or credentials</td>
  </tr>
</table>


### **Decentralized Identity Management (DIDM)**

DID lay the foundation for Decentralized Identity Management (DIDM). The DIDM layer addresses the gaps identified in the table above. It includes the following major elements:

1. **DIDM service endpoints.** Although the blockchain itself may not be an ideal platform for a full decentralized identity management service, a DID document can point to one or more endpoints where a DIDM service is available. DIDM endpoints can use cloud-based hosting or P2P protocols like Telehash for availability and scalability.

2. **DIDM protocols.** The DID document can also specify the identity protocol(s) available at any endpoint. Candidate protocols include web identity protocols (SAML, OpenID Connect, and OAuth) and semantic graph protocols (Linked Data Platform and XDI).

3. **DIDM claims dictionaries.** Claims dictionaries can help establish interoperability across a DIDM ecosystem, both within a protocol and potentially across protocols.

4. **DIDM policy templates.** Policy templates can do for interoperability of access and authorization policies what claims dictionaries do for interoperability of claims.

A combination of DID and DIDM services more fully address information security and privacy principles. 

<table>
  <tr>
    <td>Principle</td>
    <td>Provided by DID</td>
    <td>Provided by DIDM</td>
  </tr>
  <tr>
    <td>Confidentiality</td>
    <td>A master hierarchical deterministic (HD) public key associated with a principal’s identity can be used to generate child keys to encrypt data and claims</td>
    <td>Additional key management features such as HD key generation, key rolling, key delegation, and key recovery</td>
  </tr>
  <tr>
    <td>Integrity</td>
    <td>The master HD public key associated with a principal’s identity can be used to validate changes to the DID document </td>
    <td>Additional key management features such as HD key generation, key rolling, key delegation, and key recovery</td>
  </tr>
  <tr>
    <td>Availability</td>
    <td>Very high availability due to P2P distribution of the blockchain</td>
    <td>High availability of identity attributes and claims via cloud-based DIDM endpoints</td>
  </tr>
  <tr>
    <td>Non-repudiation</td>
    <td>Provides non-repudiation of the original DID registration transaction and subsequent changes through proof-of-existence</td>
    <td>Binds an identity to attributes that can be used for non-repudiation of actions taken with the principal’s private key(s)</td>
  </tr>
  <tr>
    <td>Provenance</td>
    <td>Static proof-of-existence claims of original DID registration and changes</td>
    <td>Proof of provenance for identity attributes and claims bound to a DID</td>
  </tr>
  <tr>
    <td>Pseudonymity</td>
    <td>Partially addressed by registration of pseudonymous DIDs</td>
    <td>Management of pseudonymous DIDs (performed off-chain to preserve privacy)</td>
  </tr>
  <tr>
    <td>Selective disclosure</td>
    <td>Partially supports selective disclosure through the use of one-time child keys to prevent correlation</td>
    <td>Control over disclosure of private attributes and claims bound to a DID (performed off-chain to preserve privacy)</td>
  </tr>
</table>


## **How This Innovation Compares to the State of the Art**

From the perspective of identity, security and privacy management, there has never been widely available infrastructure in which the root record for a principal is not registered with a centralized identity provider of some kind, whether a DNS registrar, certificate authority, telecom provider, email provider, social network, or some other type of service provider.

The incumbent Web identity and security management protocols (SAML, OpenID Connect, UMA) assume the existence of such a role. Although these protocols allow the actual hosting of the identity provider to be distributed, in practice the attendant usability and security problems have favored centralization.

The newer semantic graph protocols (Linked Data Platform, XDI), while architected to operate in peer-to-peer decentralized systems, do not themselves offer a solution to the fully decentralized registration and resolution of DIDs and DID documents. 

So the emergence of DID and DIDM infrastructure can remove the current dependence on centralized identity providers and "democratize" identity, attribute, and credential management so that it becomes more reliable, available, and economical.

