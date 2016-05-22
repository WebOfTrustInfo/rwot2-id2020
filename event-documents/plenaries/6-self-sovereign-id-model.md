**Main Parties**

*Issuers.* Issue verifiable claims to holders. E.g., DMV says you're a driver, UN says you're a refugee.

*Holder.* Person who holds credentials. 

*Repository.* Where a Holder stores a verifiable claim. Cannot lock Holder in. (_Container_)
The only person who interacts with Repository (for now) is the Holder!

*Inspector.* Look at credential to verify it for validity. May be Issuer. 

**The Tech**

*DID Registry.* Allocates identifiers. An assignment authority to ensure uniqueness.
Issuer, Holder, and Inspector work with it to issue and verify DID. (DID = Decentralized Identifier.)

*Public Ledgers.* Some credentials may be issued into public ledgers. For example, information ona  debarred doctor.
This is a _controversial_ part of the model.

**Optional Parties**

*Relying Party.* Party who delegates inspection to an Inspector because they don't have competency themselves.
(_Bar is Relying Party, Bouncer is Inspector_)

*Witness.* Another form of subsidiary issuer.

See [the full paper](https://github.com/WebOfTrustInfo/ID2020DesignWorkshop/blob/master/topics-and-advance-readings/a-self-sovereign-identity-architecture.pdf)

See [the use cases](http://w3c.github.io/webpayments-ig/VCTF/use-cases/)

**Possible Topics Coming Out of This**

- Terminology
- Recovery + Rotation
- Revocation
- Consent + Privacy + Visibility
- Public Ledger Reposition
- DIDs + Ledgers
- Containers
- Flows
- Use Cases

