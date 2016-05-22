**What is ID?** [Lead Editor: Marta]

Many types.

Boil down to a small set of IDs.
(Legal ID, licenses, physical + social ID, etc.)

Created a table for defining identities

**_Only the digital ID really matches how we want ID to work._**

Does that mean self-sovereign ID can only exist in virtual space?

A self-sovereign identity is more under person's control
Than their meatspace self!

**Identity Container & Relations in DID** [Lead Editor: Adrian]

How to link ID to identity container

Use case: Doctor writes prescriptions
Leaves behind a compliance element

Two DIDs: doctor, patient

Use Experience
1.) Invitation that creates container
2.) Provision identity container

Recurring:
3.) Transaction: prescription written, filled
4.) Persistent ledger entries

By introducing container
Can reduce some of the trust in centralized ledger

**Identity Graphs** [Lead Editor: Markus]

Try to model parts of identity in a unified way
Start with a personal graph
Then create a relationship graph

Can use an "overlay graph" to show relations that
Don't exist on virtual sites

Can create graphs about others

Can create views of graphs

Result: _verifiable claims_

**Cheap Verification** [Lead Editor: Greg S.]

False idea that digital security is expensive
This idea has lead to CAs being able to gouge money

There is literally no need for authorities to secure internet connections
_Security authorities create insecurity!_

Doesn't like idea of people serving DIDs either
Says they're just new DIDs

**Self-Sovereign Identity Architecture 2.0** [Lead Editor: Dave C., but just going back to Manu, Justin Has Updates]

Continue to expand on Manu's paper. 

Goal is to reduce to most salient boxes for model.
- So removed Registry
- It's now part of Oracle
- But Oracle does more, has Generators, Filestore

Dynamic Roles: One person can flip between roles

**Identity as Correlation** [Lead Editor: Adrian]

[will meet in two weeks]

**DID** [Lead Editor: Drummond]

Goals
1. The structure of an identifier (DID) creates a independent, discoverable, unique key for a value
2. The associative value must do four things:
- Prove ownership of value cryptographically: "Genesis Claim"
- Provie + update DIDs
- Point to other claims
- Point to other DIDs

Almost like a personal blockchain!
- Taking avantage of other consensuses + proofs of work

The debate: how much do we put in "head" object, 
As opposed to DID log as a whole
(It's an open architectural question)

[will do paper + specs]

**Uses Cases for Nairobi** [Lead Editor: Wayne Hennesy]

Problems in Nairobi

[2 page paper done]

Other Stuff That Will Be Papers
**HD Keys** [Lead Editor: Kiara]
**DID Use Cases** [Lead Editor: Joe, Jonathan]
Revise **Smart Signatures** [Lead Editor: Chris, Ryan]
