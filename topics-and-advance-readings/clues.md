I would like to thank all the friends that have supported this late unstructed draft submission over not submitting anything :)

# Clues

> Clue: something that serves to guide or direct in the solution of a problem or mystery.

The purpose of this paper is not to present final solutions, but to outline relevant directions, clues, that will guide us there. 

Note, this is an informal list of clues I have collected on content-addressable web and decentralized user security; for a matter of timing and future non-technical audiences reading this, clues will be short, unrelated and written in simple language. Forgive convoluted explanation.

# Clues on the content-addressable web

This first section is about clues towards a content-addressable web and is product of conversations with Juan Benet, Steven Allen, David Clark and Gerry Sussman

> 1 The way we point to things should not be bound to a location

The architecture of the web today forces us to use `URL`s when pointing to things. This implicitly forces us to only look in one particular place for one specific resource. The `L` at the end stands for `L`ocation, more specifically, one particular DNS name and the set of locations specified by its owner. Outside of the web, when we point to things, we use the name of the objects instead of the place where we can find it.

Consider buying a book and knowing that its name is `library1.com/book-12345` instead of having a name that you can try to find in several libraries - exactly like ISBN.

If we can assign different names to distinct resources that everyone could agree upon (e.g. for example hash functions applied to its content) then, it doesn't matter where the content, since it could be on multiple locations. Having one singular location is a single point of failure, since that location could disappear, be censored and alterated.

> 2 Owners should not be the sole distributors of content.

It is clear that in a decentralized web content can be distributed by whoever can prove they have the right content.
In the case of hashes, users will check if the hash of the content received is the same as the one they asked for.

> 3 The problem of naming things and the problem of finding things should be separate problems.

There are multiple ways to find something we know the name of. Keeping these problem separate make us distinguish two important ortoghonal layers, __naming__ and __discovery__.

To get a `Book X`, we could ask our friends (closed network), we could go to a particular library (directory), or ask to a global network of peers (dht, gossip & family) and so on.

Existing working projects have pioneered this are such as IPFS - which is often confused to be a DHT, while it is a _naming_ system and a particular _discovery_ for these names. The discovery bit in IPFS is and should be always be swappable.

Note: So far we have discussed of immutable content, there are also working tricks for mutable content. To learn more about this, read about [IPFS](https://ipfs.io) and [IPLD](https://github.com/ipfs/specs/tree/master/ipld).

## Many little webs

This section expands on separating naming from discovery and shows cases where global discovery is not needed.

Having names that are not bound to a location, means that we could get the content from multiple locations, but how can we find these multiple locations in first place? Global resolvers (like the DHT in IPFS) could help us find the content, however there are plenty of use cases for which there is no need to ask to a huge network of nodes if we can find someone (a smaller subset of the global network) that have the content we are looking for.

These are smaller networks that that I call __"little webs"__.

> 4 One should not need to be connected to a global network to retrieve local content

If all the hashes that are used in a graph of resources pointing to each others can be found in the network, this network is a "little web". By definition a global DHT is a "little web".

If we are in a local network and we create and distribute content with each other, we can use hashes to point to things. In this way, if we need to resolve a hash, we can ask to the local network to resolve that hash and any peer can serve it, since we can authenticate the content with its name. In this case, since this local area network can resolve any hash used, it is a "little web".

There are plenty of other "little webs", in which using hashes to point to things is either already happening or could be applied to. In blockchains we could point to previous transactions, or contracts by using hashes and these can be resolved just from having the chain (if a hash point to a previous transaction, we know the hash of that transaction since it is in the log). A `git` repository it itself a self-contained "little web".

> 5 Hence the global network could be partitioned.

One does not need to be connected to the main web. As long as hashes can be resolved in any "little web". This would not be possible with the HTTP-web.

## Unpredictable hashes

This is a reminder that hashes are not secrets

> 6 If there exist one peer willing to serve a hash, all the network has access to the content it points to.

Using hashes to point to content, makes our pointers predictable. While the resolution of a URL can stand behind access control enforced by the server, hashes can't. The URL http://nicola.com/personal/things may not be resolved, while if there exist one peer that is willing to serve the content behind `hashPersonalThingsOfNicolaXYZYZYZYZY..`, then all the network can have access to it.

Here are different solutions I propose we could build interesting scheme for:

- Encrypted hash: one could encrypt a hash with a secret key that is shared across the party involved. In this way, peers can still use hashes to point to things, but these hashes will be encrypted with a secret. In order to resolve them, they would need to unwrap the encrypted hash and ask to the network about it.
- Fresh hash: one appends a fresh cryptographic nonce (random padding) to decrease the chances of having other peers being able to resolve hashes (or correlate them with ones that they have already seen)
- Encrypted content: the content is encrypted so even if it is found, it won't matter (the two methods above could be combined with this, depending on what is our security model)


## Solving cycles

> 7 Things should be able to point to each other

One can't hash two resources that point to each other using hashes.

```
QmBobZYX                              QmAliceZYX
+----------------------+              +----------------------+
|                      |              |                      |
| friends [QmAliceZYX <----------------> friends [QmBobZYX   |
|                ....] |              |                ....] |
+----------------------+              +----------------------+
```

One could assign identifiers to a resources, but it would be tricky not to run into other problems.
My simples solution is the following:

- Add a third node that will link to `QmBobZYX` and `QmAliceZYX`
- Replace `QmAliceZYX` and `QmBobZYX` with relative paths (so `../alice` and `../bob`)
- Now, since neither alice or bob contain hashes, then we can hash them separately
- Make the new root point to the hashes of alice and bob `{alice: AliceBlob,  bob: BobBlob}.
- Finally hash this root (so that we have a merkle graph)

With this little trick, we can now refer to bob with `QmRootXYZ/bob`.
Using this particular scheme we have a need of coming up with a path scheme.

[Note for the event: are there better ways to do this?]

## Nice paths

I will not repeat the work done by [IPLD](https://github.com/ipfs/specs/tree/master/ipld) and that I proposed as merkle-paths.

In this section, I will just point out to conversations that have plenty of clues on how such path scheme should look like.
The work done is around [IPLD](https://github.com/ipfs/specs/tree/master/ipld) and my initial generalized version of [cross data-paths](https://github.com/nicola/cross-data-paths) and the [final agreement](https://github.com/ipfs/specs/issues/97). There is definitely something to learn from this effort.

> 8 Path scheme should allow to describe the lower level and the higher level representation

This is the important challenge of providing a way to point to the low level and the high level representation of data.
The following link is a submission by itself: [Separating high-level from low level representation](https://github.com/ipfs/specs/issues/91)

--

# Clues on using identity

The following set of clues are from my draft on the [decentralized user security model](https://github.com/nicola/decentralized-user-security-model). In other words, clues on how decentralized application should interface with the user data.

> 1. (least privilege) Nothing is allowed, unless permitted


> 2. (user confirmation) Permissions are granted only after the user confirms


> 3. (explicit authentication) Identity is never exposed, unless permitted


> 4. (explicit authorization) Data is always private by default, no one has access to it or parts of it, unless permitted


> 5. (explicit delegation) No one can impersonate the user and operate in their behalf, unless permitted


> 6. (encryption by default) Any intermediary, the host of the data or the network provider, if any, have no access to any data, unless permitted


> 7. (confidentiality by default) Shared data is only accessible by the parties involved


> 8. (integrity by default) Users must know if their data has been altered

[Note for the event: these are points that I would like to discuss and confront to the Self-sovereign identity model]

--

# Topics of further discussion

> Causal chains: We shouldn't use blockchain technology, unless global ordering is needed

--

Notes: this document has been written all in one go and it went through little grammatical checking. I will be cleaning the document and simplifying the concept expressed in the near future.

Nicola Greco
- keep on rocking the decentralized web
