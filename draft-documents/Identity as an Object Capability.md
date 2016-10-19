Identity as an Object Capability
================================

How to create a sovereign identity / information system on a capability oriented distributed computing platform.
------------------------------------------------------------------------
by Pekko Koskinen, Jorge Lopez


Views / Points that this paper intends to make.

* The concept of identity collates, as we currently use it, collates two very different functions: 
    * Identity on its simplest form, represented as information, functions as a unique identifier. Different contexts / applications require different information associated to a unique identifier in order to fulfill their goals.
    * Identity is also a distribution of information, connected to that identifier. This information, as representation of “ourselves”, is critically a question of rights and control over that data.
* An application should not require more information than what it is needed to fulfill its explicit goals, in order to preserve privacy.
* A user may have/control multiple identities.
* In order to maintain privacy, the control on how these identities can be associated to each other.
* Authentication is a mechanism by which an agent can establish / prove identity.
* To allow for self sovereign identity, an agent must be able to control the information associated with its identity (both access, and modification to its contents).
* On an object capability system, the information associated with an identity, is a capability(s) that an agent grants to another (i.e. an application).
* This means that the agent may have exclusive control over this information, for as long as it is able to authenticate. The application may interact with this information only through the capabilities given to it.
* Utilizing object capabilities allows for  agents to have full control over the information they share with others, while having fine grained control over how other may access, or modify this information.
* “Smart Contracts” can give control of how identifying information is to be utilized, although trust is required that the application's node is non-malicious, and thus not leaking the information “under the hood”.
* Capabilities can be revoked, allowing the agent to restrict access to identifying information.
* Capabilities can also be shared, allowing the agent to share the same information with multiple parties in a verifiable and non repudiable way.
* Cryptographic capabilities as authentication and identity control medium.
* Transmission of identity using capabilities (Capabilities as Public Key infrastructure): http://www.erights.org/elib/capability/ode/ode-pki.html



Architectural Notes on Identity:
--------------------------------

The nature of identity on internet is altogether a different animal from the identity in the physical world. In the physical world, identity generally builds out of situations with relatively few participants. These situtations rarely leave strict records, only memories of their participants. These memories are then shared not as remembered versions of what took place (a manner of recalling which is only used by necessity), but collated to an interpretation engine for opinionating upon the persons encountered.


The construction process of an identity online stems from very different sources. The encounters are generally narrow in their channels (text, sound, perhaps video), but present a possibility of a much wider distribution: even if the encounter does not originally reach that many pairs of eyes, it often stays as a record that the identity is considered personally beholden to. The record also provides means of distribution into other context, perhaps years later. Essentially, the interactions (besides private calls etc.) share a published nature.


As more and more of our operative identity is based on online structures, the pragmatic nature of identity also shifts in quality closer to that basis. Therefore any architecture of identity has to keep in mind it's gestalt operative nature -- they're potentially building a significant piece in the puzzle of being human.


Inescapably Artificial:
-----------------------

Online, every basis of identity is an artificial, designed framework -- a template. This feature is a significant factor in what makes us different in Linkedin from Facebook, Reddit etc. The content we create is only part of that difference, and even that content is created under the strong suggestive nature of the framework itself, which also includes the equally artificial and designed social environment.



A Managed, Networked Collective:
--------------------------------

Online identity is inherently a network. While there are common points of access and collective interfaces, the whole collects out of its pieces: a comment here, a video there. Of course, we parse the identity together in the physical world as well, from different encounters. However, the generally recorded nature of the pieces online changes the nature of that parsing. Instead of passing moments, it's a persistently present patchwork, constantly being parsed by other people. This gives the identity a quality that closely relates to the concept of management -- we are increasingly in a managerial relation with our presence in the world.



The Ownership/Control over the Data of Identity:
------------------------------------------------

Let's first address this issue by two key points that lay the groundwork for it:


1. The ownership, or control over the data that composes that identity is arguably a right. It is not approached as such currently, but this is against the operative basis we have socially relied upon in our societal structures. This right is even more important when that data is persistently recorded.


2. The value of data is not only relevant to the individuals that pertain to their identities. It is also relevant as data of general research. The possibilities of being able to aggregate the massive amounts of data we're producing is of immense social value. Of course, the rights of access to the data are a concern in relation to this value. But the decision of that sharing is most aptly connected to the individuals who hold the control of that identity, allowing them to decide what to share, who to share it with, with what value (social, not just monetary), and how to share it (whether it is traceable back to the identity itself or not, for example).


There's a lot of potential structural flexibility that can be applied to such sharing: sharing your data with a specific organization, that further shares it as an aggregate etc. But the key value is that the nature of such sharing should be perceivable to the ones that the data directly pertains to. 


Observing this point more generally, the extensive fragmentation of such data to various islands of ownership, which summarily describes the current situation, is an obvious loss of collective value from collective production. These islands aggregate together whatever data they have, but their collections are usually arbitrary arrangements (oriented by the platforms and companies that control these islands, without any particular balancing), which makes the aggregation inherently skewed and partial. As a social design this is an obviously undesirable situation.


Of course, these points are of summary nature, and lack many of the details that significantly affect the situation. For example, a data that is once shared has a "spilled milk" quality to its behavior -- it's often impossible to get it back to the bottle (it's arguable that this quality is even desirable, and that the additional processes of distributions are more healthy than toxic). But they serve to highlight two topics that result from these points: 1. The inversion in terms of rights to the data that concretely forms the building blocks other people use to construct your identity -- what makes you, in essence, you — is not controlled by yourself. 2. The inherent fragmentation of socially valuable data to skewed sets under isolated ownerships, which makes their aggregation both problematic and out of general usability.
