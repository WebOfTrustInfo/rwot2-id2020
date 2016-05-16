
# Questions around key management for digital identity systems

**By Christian Lundkvist & Rouven Heck**

Here we go over some topics related to key management and related questions for future discussions.

## Multiple Personas/Identities

In order to facilitate privacy it is useful to let the user be able to create multiple unlinked identities to be used for different purposes. Some questions/challenges around this:

1. How should the user practically manage the keys of multiple identities (assuming for simplicity that one key controls one identity)

1. HD wallets are a good method of managing a virtually unlimited number of keys. If HD wallets are used, should the user be responsible for storing and maintaining the seed? Is this too much of a burden for the user?

1. If the user loses their HD wallet seed, can there be a reset feature that restores all their identities/personas? If so, how would this recovery work?

1. A Shamir Secret Sharing scheme can be used to recover the seed from a threshold of recovery members holding pieces of the seed. This protects against loss, but not against compromise. Is there a good way that the seed can be *replaced* instead of reconstructed to also protect against compromise (similar to discussion about key recovery)?

## Recovering lost keys

In a robust identity system we cannot have the situation where if you lose your phone you also lose your identity. Thus we need to build systems where the user can have a means of recovery of their identity even with loss of all their keys.

Using a blockchain platform like Ethereum you can accomplish something like this through the following method:

* Use the address of a smart contract as a cryptographic identifier, creating a level of indirection between the cryptographic identifier of the identity and the private keys controlling that identifier.

* A private key (user key) is used to access and control the smart contract, so the user still needs to control a private key, and this private key is the ultimate core of the identity.

* The smart contract contain a list of (say) 3 delegates (other identities). Two of the three of these delegates can send a message to the smart contract with a replacement user key. This way if the user loses their key they can still recover.

Some questions around this system:

1. If your delegates collude against you they can take over your identity. Is this something we want to guard against? If so, how do we guard against it while still allowing the delegates to reset your key in the case of total key loss?

1. Are there good methods from existing "Account Recovery" workflows in traditional webservices that can be leveraged to provide improved workflows for key recovery in decentralized identity systems? For instance Gmail can be set up to allow access for third parties after a time of inactivity.

1. It is worth exploring other ways of defining a recovery network besides having the user do it explicitly. For instance you could have a simple notion of a "friend link" or "connection" that can define the users social graph and be define throughout the users historical interactions. Could the identities in this graph provide a recovery network? What would be the threshold number to use in this setting? This is something that Christopher Allen and others are exploring.

## Signing keys vs encryption keys

An identity would use a signing keys to sign claims and attestations, and authorize themselves to protected resources or systems like blockchains that require access control. An identity could also have encryption keys that they would use to receive encrypted messages and to access encrypted resources.

Recovery of encryption keys is a different process than recovery of signing keys. When recovering signing keys you technically only need to replace the key with a new one and make sure the system marks the new one as having the capabilities of the old.
If you have encrypted something with an encryption key and you lose that key you will lose the ability to decrypt that data. Thus in this case you are required to recreate the key and not just produce a new key.

Questions:

1. What are the best way of handling encryption keys for the user? Should encryption keys and signing keys be generated from the same seed/entropy?

1. How to help the user if they lose their encryption key? One way is to have a Shamir Secret Sharing between the users delegates.

1. Are there current key-management best practices (for instance in end-2-end encrypted messaging clients) that can be leveraged and adapted for the decentralized case?
