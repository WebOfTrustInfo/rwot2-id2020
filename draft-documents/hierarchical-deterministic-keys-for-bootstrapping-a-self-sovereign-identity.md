# Hierarchical Deterministic Keys for Bootstrapping a Self-Sovereign Identity

v0.1 June 14, 2016

---

**Abstract.** Hierarchical deterministic (HD) keys are a type of deterministic bitcoin wallet derived from a known seed that allow for the creation of child keys from a parent key. Because the child key is generated from a known seed there is a relationship between the parent and child keys that is invisible to anyone without that seed. The HD protocol (BIP0032) can generate a nearly infinite number of child keys with a deterministically-generated seed (or chain code) from its parent, providing the functionality of being able to recreate those exact same child keys as long as you know the seed. 

In the context of Bitcoin, HD keys are predominately used to simplify wallet backups. Because the child key can operate independently and the parent key has the ability to monitor and control each child key, that parent key can still continue to operate even if the child key is compromised. If we use a blockchain token to represent a person or an identity, the root HD key facilitates the creation and control of an identity that can then create subsequent child identities or personas depending on the context of the identity use case.

---

#### 1. Introduction

HD keys (or wallets) are defined by the BIP0032 standard for Bitcoin. 

![](https://raw.githubusercontent.com/bitcoin/bips/master/bip-0032/derivation.png)

**BIP0032** Specifies a system for deriving a tree of key pairs from a single seed.

There are two major benefits of using HD Bitcoin wallets over random non-deterministic or random wallets. The first is that the user can create and use public keys without having to access the corresponding private key. This makes for more secure usage on a server: since the public keys are generated for each transaction in a receive-only capacity the server does not need any of the private keys to spend the funds. The second benefit is in prudent key management. HD keys allow for the user to securely hand out child keys with no risk to the parent key. If a child key is lost or compromised it can be derived again from its parent.

However, HD keys can go beyond Bitcoin. In 1991, PGP was the first piece of software to introduce the concept of identity-based cryptography by associating an individual to a cryptographic key pair for encrypted communication. One significant impediment to the general adoption of identity-based cryptography was its dependence on a public-key infrastructure — the set of procedures needed to create, manage, distribute, use, store, revoke, and manage keys. Because HD keys relate to identity, the possible improvements in key management improve the related problems around public-key infrastructure in identity.

#### 2. Use-cases

**Browser Authorization.**
HD keys allow for greater control on the part of the user, since the parent keys can easily revoke its child keys. An individual can give their browser a key pair and permission to sign certificates with a newly generated child from that key pair each time. If the user ever wants to revoke that ability their parent key can revoke the authority of the child key it gave to the browser.

**Multiple Personas.**
In an identity system where the user creates and manages multiple identities for different purposes, separating child keys to create  distinct persona would allow for a greater degree of control and manageability for the user while maintaining privacy between the individual personas.

**Governance.**
In the context of governments, corporations, or families, the built-in hierarchy of HD keys could mirror a real-life separation of control. It could also express meaning: branches of keys can be used to separate different departments in these various systems. Finally, it can offer a crypto identity for related financial systems.  

**Credit Reputation.**
Bitcoin has prided itself on letting users 'be their own bank'. Cryptocurrency currently allows users to 'make deposits', transfer money, and prove ownership, yet there is no possibility of a credit system without identity. In managing a credit reputation, a borrower's repayment history is the basis of an individual's financial reputation for lenders to use when determining financial risk. It is possible to manage and prove an individual's credit history with HD keys by fragmenting a part of a user's identity into individual payments with child keys, then revealing some larger part of their identity with its parent key when it's required or relevant.

#### 2. Identity Models

Identities can be represented at any key pair of a hierarchical deterministic key set. In the future, we may want to set a standard for the identity keypair to be a different keypair than the master one.

**1.1 Self-Sovereign Model.** 
The BIP0032 standard states that a key hierarchy can be derived at a depth from 0 to 3. Placing the individual at the core root of the derivation (depth 0), where the user is the holder of the seed and master key is the self-sovereign identity model. Here the user has the greatest degree of control and responsibility in managing their identity client-side.

**1.2 Trusted Third-party Model.**
Placing the individual at a depth of 1 is the trusted third-party model. In some cases where an individual is not capable of managing their own keys on their device, this may be appropriate while also compromising on the degree of immediate access an individual has over their identity.

#### References
---

Allen, Christopher. "[Principles of Self-Sovereign Identity](https://github.com/ChristopherA/self-sovereign-identity)." 2016.

Allen, Christopher and Appelcline, Shannon. "[Hierarchical Deterministic Keys: BIP32 & Beyond](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/topics-and-advance-readings/hierarchical-deterministic-keys--bip32-and-beyond.md)" 2015.

Lundkvist, Christian and Heck, Rouven. "[Questions around key management for digital identity systems](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/068c409acc117c81cf7a95e1c00f647d1557a943/topics-and-advance-readings/Identity-Property-Simulation.md)". 2015.

Shea, Ryan. "[Selective Disclosure of Identity with Hierarchical Deterministic Keys and JSON Web Tokens](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/topics-and-advance-readings/Selective-Disclosure-of-Identity.md)". 2015.


Wuille, Pieter. "[Hierarchical Deterministic Wallets](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)". 2016.
