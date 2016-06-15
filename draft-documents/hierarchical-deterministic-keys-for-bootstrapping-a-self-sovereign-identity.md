# Hierarchical Deterministic Keys for Bootstrapping a Self-Sovereign Identity

v0.1 June 14, 2016

---

**Abstract.** Hierarchical deterministic (HD) keys are a type of deterministic bitcoin wallet derived from a known seed, that allow for the creation of child keys from a parent key. Because the child key is generated from a known seed there is a relationship between the child and parent keys that is invisible to anyone without that seed. The HD protocol ( BIP0032) can generate a nearly infinite number of child keys that with a deterministically-generated seed (or chain code) from its parent, providing the functionality of being able to recreate those exact same child keys as long as you know the seed. 

In the context of Bitcoin, HD keys are predominately used to simplify wallet backups. Because the child key can operate independently and the parent key has the ability to monitor and control each child key, that parent key can still continue to operate even if the child key is compromised. If we use a blockchain token to represent a person or an identity, instead of a financial value, the root HD key facilities the creation and control of an identity that can then create subsequent child identities or personas depending on the context of the identity use case.

---

#### 1. Introduction

HD keys (or wallets) are defined by the BIP0032 standard. There are major two benefits of using HD wallets over random non-deterministic or random wallets. The first is that the user can create and use public keys without having to access the corresponding private key. This makes for more secure usage on a server since the public keys are generated for each transaction in a receive only capacity the server doesn't have any of the private keys to spend the funds. The second benefit is in prudent key management. HD keys allow for the user to  securely hand out child keys with no risk to the parent key. If a child key is lost or compromised it can be derived again from its parent.

As these properties relate to identity, we exchange the wallet with an individual or entity. Given the ten principles of self-sovereign identity, below is a binary rating of whether or not that qualification is met my HD keys.

|                  | [Principles of Self-Sovereign Identity](https://github.com/ChristopherA/self-sovereign-identity)                         | Fulfilled by HD Keys |
|------------------|---------------------------------------------------------------|----------------------|
| Existence        | Users must have an independent existence                      | x                    |
| Control          | Users must control their identities                           | x                    |
| Access           | Users must have access to their own data                      | x                    |
| Transparency     | Systems and algorithms must be transparent.                   | x                    |
| Persistence      | Identities must be long-lived                                 | x                    |
| Portability      | Information and services about identity must be transportable | o                    |
| Interoperability | Identities should be as widely usable as possible             | x                    |
| Consent          | Users must agree to the use of their identity                 | x                    |
| Minimization   | Disclosure of claims must be minimized                        | x                    |
| Protection       | The rights of users must be protected                         | o                    |

**1.1 Self-Sovereign Model.** 
The BIP0032 standard states that a key hierarchy can be derived a depth from 0 to 3. Placing the individual at the core root of the derivation (p0), where the user is the holder of the seed and master key is the self-sovereign identity model. Here the user has the greatest degree of control and responsibility in managing their identity client-side.

**1.2 Trusted Third Party Model.**
Placing the individual at a depth of p1 is the trusted third party model. In some cases where an individual is not capable of managing their own keys on their device, this may be appropriate while also compromising on the degree of immediate access an individual has over their identity.

#### 2. Use-cases

**2.1 Current Implementations**

**[Datt v0.1.0.](https://engineering.yours.network/articles/2015-12-11-prototype/)** The Datt is an open-source, decentralized content sharing platform with integrated bitcoin payments. The Datt network includes cryptoidentities derived from HD Keys where the master key pair that is held client-side.

**2.2 Possible Implementations**

**[Multiple Personas](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/068c409acc117c81cf7a95e1c00f647d1557a943/topics-and-advance-readings/Selective-Disclosure-of-Identity.md).**
In an identity system where the user creates and manages multiple identities for different purposes, the separation of child keys to creating separate distinct persona would allow for a greater degree of control and manageability for the user while maintaining privacy between the individual personas.

**Governance.**
In the context of governments, corporations, or families, the built-in hierarchy in HD keys could mirror the separation of control and offer a crypto identity in these financial systems. The hierarchical tree structure can express meaning, branches of keys can be used to separate different departments in these various systems.

**Credit Reputation.**
In part, Bitcoin has prided itself on letting users 'be their own bank'. Cryptocurrency currently allows users to 'make deposits', transfer money, and prove ownership yet there is no possibility of a credit system without identity.

In managing a credit reputation a borrower's repayment history is the basis of an individual's financial reputation for lenders to use when determining financial risk. It is possible to manage and prove an individual's credit history with HD keys by fragmenting a part of a user's identity into individual payments with child keys then revealing some larger part of their identity with its parent key when its required or relevant.
