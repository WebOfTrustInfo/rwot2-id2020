# Hierarchical Deterministic Keys for Bootstrapping a Self-Sovereign Identity

v0.2 July 18, 2016

--- 

### Abstract.

In the context of Bitcoin, Hierarchical deterministic (HD) keys are predominately used to simplify wallet backups. Because the child key can operate independently and the parent key has the ability to monitor and control each child key, that parent key can still continue to operate even if the child key is compromised. When a Bitcoin or similar blockchain token is used to represent a person or an identity, the master HD key facilitates the creation and control of an identity that can then create subsequent child identities or personas. HD keys simplify key management in Bitcoin, and when HD keys are used to represent an identity it simplifies identity management on a blockchain.

---

### Introduction

In 1991, PGP was the first piece of software to introduce the concept of identity-based cryptography by associating an individual to a cryptographic key pair for encrypted communication. One significant impediment to adoption of identity-based cryptography was its dependence on a centralized public-key infrastructure. The set of procedures needed to create, manage, distribute, use, store, revoke, and manage keys all take place locally to the user, then need to be broadcasted to the centralized public-key server.

The blockchain offers a solution to the centralized public-key infrastructure by decentralizing key management. When HD keys are implemented on a blockchain specific to identity, key management is improved further still.

There are two primary benefits of using HD keys over random non-deterministic keys. 

1. Improved privacy
	- Because the child key is generated from a known seed there is a relationship between the parent and child keys that is invisible to anyone without that seed. 
	- HD keys allow the user to securely hand out child keys with no risk to the parent key. This makes for greater security usage on a server: since the public keys are generated for each transaction in a receive-only capacity the server does not have any of the private keys to spend those funds.
	
2. Prudent key management
	- If a child key is lost or compromised it can be derived again from its parent, providing the functionality of revocation and recovery of those exact child keys with ownership of the seed.
	- Best practices with bitcoin wallets dictate that each key be considered single use and HD keys offer a unification of all the keys under a users control.

For Bitcoin, HD keys are functionally master wallets defined by the BIP0032 standard. 

**BIP0032** Specifies a system for deriving a tree of key pairs from a single seed.

The HD keys can generate a nearly infinite number of child keys from its parent, although BIP0032 standardizes this at three max deviations. 

The standard or specific blockchain where HD key are used is somewhat less relevant than the functionality of the HD keys themselves. The BIP0032 standard was designed specifically for Bitcoin transactions and to create a uniformity of Bitcoin wallets. Implementations of HD keys on blockchains specifically designed for identity may take a verity of different approaches to their HD key targeted uses, derivations, and standards. 

### 1. Derivations and Standards

[Still Drafting..]

### 2. Identity Models

Identities can be represented at any key pair of a hierarchical deterministic key set. Because the master key has the control of every subsequent child key, position of the master key is the only form of truly self-sovereign identity model. For use cases where the user chooses to differ key management of the master key to a third party such that they control one of the child keys of the master, they do so by compromising on the degree of access an individual has over their keys and related identity. 

![](http://i.imgur.com/cgvgbWf.jpg?1)

**1.1 Self-Sovereign Model.** 
Placing the individual at the core root of the derivation (depth 0), where the user is the holder of the seed and master key is the self-sovereign identity model. Here the user has the greatest degree of control and responsibility in managing their identity client-side.

**1.2 Trusted Third-party Model.**
Placing the individual at a depth of 1 or any subsequent derivation is the trusted third-party model. In some cases where an individual is not willing or capable of managing their own keys on their device.

### 3. Use-cases

**Browser Authorization.**
HD keys allow for greater control on the part of the user since the parent keys can easily revoke its child keys. An individual can give their browser a key pair and permission to sign certificates with a newly generated child from that key pair each time. If the user ever wants to revoke that ability their parent key can revoke the authority of the child key it gave to the browser.

**Multiple Personas.**
In an identity system where the user creates and manages multiple identities for different purposes, separating child keys to create a distinct persona would allow for a greater degree of control and manageability for the user while maintaining privacy between the individual personas.

**Governance.**
In the context of governments, corporations, or families, the built-in hierarchy of HD keys could mirror a real-life separation of control. It could also express meaning: branches of keys can be used to separate different departments in these various systems. Finally, it can offer a crypto identity for related financial systems.  

**Credit Reputation.**
Bitcoin has prided itself on letting users 'be their own bank'. Cryptocurrency currently allows users to 'make deposits', transfer money, and prove ownership, yet there is no possibility of a credit system without identity. In managing a credit reputation, a borrower's repayment history is the basis of an individual's financial reputation for lenders to use when determining financial risk. It is possible to manage and prove an individual's credit history with HD keys by fragmenting a part of a user's identity into individual payments with child keys, then revealing some larger part of their identity with its parent key when it's required or relevant.

### References
---

Allen, Christopher. "[Principles of Self-Sovereign Identity](https://github.com/ChristopherA/self-sovereign-identity)." 2016.

Allen, Christopher and Appelcline, Shannon. "[Hierarchical Deterministic Keys: BIP32 & Beyond](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/topics-and-advance-readings/hierarchical-deterministic-keys--bip32-and-beyond.md)" 2015.

Lundkvist, Christian and Heck, Rouven. "[Questions around key management for digital identity systems](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/068c409acc117c81cf7a95e1c00f647d1557a943/topics-and-advance-readings/Identity-Property-Simulation.md)". 2015.

Shea, Ryan. "[Selective Disclosure of Identity with Hierarchical Deterministic Keys and JSON Web Tokens](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/topics-and-advance-readings/Selective-Disclosure-of-Identity.md)". 2015.

Wuille, Pieter. "[Hierarchical Deterministic Wallets](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)". 2016.
