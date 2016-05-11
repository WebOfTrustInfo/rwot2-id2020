# No Secure Protocol = No Sovereign Identity

_Submitted by [Greg Slepak](https://twitter.com/taoeffect)_

Since this event relates in many ways to Christopher Allen's concept of a [Self-Sovereign Identity](http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html) (SSI, not to be confused with [SSI](https://en.wikipedia.org/wiki/Supplemental_Security_Income) or [SSI](http://nginx.org/en/docs/http/ngx_http_ssi_module.html)), I will make various references to it throughout, particularly to the __Ten Principles of Self-Sovereign Identity__.

### Decentralized Identities Require A Secure Protocol

The second principle of an SSI, says Allen, is __Control__:

> Users must control their identities. Subject to well-understood and secure algorithms that ensure the continued validity of an identity and its claims, the user is the ultimate authority on their identity. They should always be able to refer to it, update it, or even hide it. They must be able to choose celebrity or privacy as they prefer. This doesn’t mean that a user controls all of the claims on their identity: other users may make claims about a user, but they should not be central to the identity itself.

It is clear that without security we cannot have an SSI, for there can be no control without security.

However, "well-understood and secure algorithms" _are necessary but insufficient_ to provide the sort of security that is necessary for SSI. Yes, you do need secure algorithms to keep identities from getting hacked, __but without a *secure protocol* we cannot have an SSI in the first place.__

After all, HTTPS/X.509 have "secure algorithms", but their lack of a secure protocol for mapping identifiers to data prevents us from using them to create Self-Sovereign Identities.

### "But Greg, we don't _need_ a protocol, just a great _implementation!"_

We definitely need a protocol. There are many great folks working on great implementations, but no matter how great those implementations are we can never have truly Self-Sovereign Identities without a secure, decentralized protocol.

Furthermore, it bears special emphasis to point out precisely _what kind_ of decentralized protocol that is needed for SSI.

For example, one could say that the wonderful folks at Blockstack have devised a secure decentralized protocol, however I believe it is insufficient on its own to serve as the protocol that's needed for SSI. Specifically, there are the following concerns:

- Blockstack's protocol does not seem to be completely decentralized, as Blockstack appears to have complete control when it comes to making changes to it.
- Blockstack's protocol appears entirely focused on the workings of a single implementation of the general concept of a blockchain (Bitcoin).
- This specific implementation (Bitcoin), could at any point fail to serve as a long-lived host platform for SSI for a large variety of reasons. Similarly, the specific implementation of Blockstack could also fail.

These concerns put into serious question whether the system is capable of supporting SSI Principles 2 (Control), 3 (Access), 5 (Persistence), 6 (Portability), 7 (Interoperability), 10 (Protection), and possibly others.

That is not to pick on Blockstack, as these same concerns would apply to _any_ blockchain-specific software or protocol.

### So What Kind Of Secure Protocol Do We Need?

At the previous [Rebooting the Web-of-Trust Design Shop](http://www.weboftrust.info/event-2015-sf) we produced a paper describing the high-level design of a __DPKI__, or a [Decentralized Public Key Infrastructure](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/final-documents/dpki.pdf), to tackle this exact problem.

DPKI describes the foundations for an Internet protocol that can use _any_ decentralized public datastore to store and retrieve identities using _the most secure method possible_ for each decentralized datastore.

We focus on blockchains specifically because unlike other decentralized datastores (such as DHTs by themselves), only blockchains are known to provide reasonable assurance of __Persistence__ (SSI Principle #5) in a decentralized manner.

### DPKI? Sounds cool! So what's next for DPKI?

At this event we would like to, at the very least, publish an updated and polished version of the DPKI paper.

Our goals are:

- Ask for peer review and fix any errata or other issues.
- LaTeX-ify the thing to give it that "proper computer science paper" feel. :)
