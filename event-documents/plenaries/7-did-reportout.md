After a discussion of Manu's DID model, groups broke out to talk about subsets of the topic

**Use Cases**

Worked to digest the existing use cases

Wanted to understand the human value
- But it felt like the tech structure was the heart

So, named each use case a
- and listed the technical topics that each use case demonstrated

Want *fewer* use cases that demonstrate everything

_Manu asks that these be sent to Verifiable Claims group._

**Overall Model**

- Issuer might make claims about claims: this is a _witness_
- Instead of Relying Party (geeky term of art): consumer, receiver
- Oracle instead of public ledger; may not be static

**Privacy**

Identity is not disclosed, claims are
- How do you protect claims from being sent on?

Choose what to disclose
But then other people get to decide whether to trust you

Systems where you have to disclose (e.g., DMV) are _different systems_.
Don't try to solve those!
- The Holder has absolute control!

**DID**

- Not Identity!
- Not Verifiable Claims!

Discoverable, uniform, random
- The value of a DID on its own is very small (when issued)

DID Object
- Have Access Control to Update it
- Point to Services that can do everything else
- Must be able to do proof of ownership
- Self-verifiable, self-validating

Debates?
- Cross-ledger friendly?
- Resilient to chain failure?
