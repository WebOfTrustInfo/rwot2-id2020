XDI Graphs in IPFS
------------------

XDI (eXtensible Data Interchange) is a technology for modeling, storing and connecting any kind of personal and organizational data.
Its underlying data model is a graph consisting of nodes and directed arcs.
XDI is well-suited for digital identity that is distributed and heterogeneous.
Through the use of mappings and connectors, XDI can be used to model even data that is not itself natively in XDI format (e.g. a Facebook profile, a government ID, or a record in a corporate database).
Traditionally, XDI assumes a network topology that involves service providers and endpoints, e.g. a connection can be established between an individual and an organization through their respective endpoints.

IPFS (InterPlanetary File System) is a distributed data store built on a combination of peer-to-peer technologies such as DHT, BitTorrent, and others.
It provides built-in support for certain higher-level data constructs, such as file systems, or Git histories.
At its core it is very flexible in terms of the type of data it can store.
IPFS uses a graph model where nodes and links represent data.
This aspect of IPFS is also known as IPLD (InterPlanetary Linked Data).

The following is an exercise to use IPFS as a data store for XDI graphs, in other words to map the XDI data model to the IPFS data model.

Mapping
-------

Even though both XDI and IPFS use graphs for expressing all data, there are differences that have to be considered for a mapping.

Data in IPFS is immutable and stored in content-addressable nodes.
Every node in the graph is identified by a hash which is calculated from the node's data plus the node's links to other nodes.
Links consist of a name plus the hash of the target node.
A node's identifier therefore transitively depends on all nodes it links to at all depths.
This means that the IPFS graph is a directed acyclic graph (Merkle DAG), in which cycles are not possible.

The XDI graph model knows two types of nodes (context nodes, literal nodes) and three types of arcs (contextual arcs, relational arcs, literal arcs).
Contextual arcs and literal arcs form the "backbone" of the graph, and relational arcs can be added between any two context nodes.

Example XDI graph with 4 contextual arcs, 2 literal arcs, and 1 relational arc (using the XDI DISPLAY serialization format):

	//=markus
	//=drummond
	=markus//<#email>
	=markus//<#tel>
	=markus<#email>/&/"markus@danubetech.com"
	=markus<#tel>/&/"+43 664 3154848"
	=markus/#friend/=drummond

	  ___               ___               ___               ___
	 |   | ----------> |   | ----------> |   | - - - - - > |   | "markus@danubetech.com"
	 |___|  =markus    |___|   <#email>  |___|     &       |___|
	   |                v |
	   |                v |
	   |        #friend v |               ___               ___
	   |                v  ------------> |   | - - - - - > |   | "+43 664 3154848"
	   |                v       <#tel>   |___|     &       |___|
	   |                ___ 
	    -------------> |   | 
	       =drummond   |___|

If one considers only the contextual and literal arcs of an XDI graph (in this example, leaving out the `#friend` relational arc, then the graph would be a tree.

In this case, the mapping to IPFS is straight-forward and can be done using the following rules:
 1. Every XDI context node is modeled as an IPFS node.
 1. Every XDI contextual arc is modeled as an IPFS link. The link's name is the identifier of the XDI contextual arc, e.g. `=markus`.
 1. Every XDI literal node and literal arc are modeled as data in the IPFS node corresponding to the XDI context node containing the XDI literal node. The key of this entry is `&`. The value of this entry is the XDI literal value, e.g. `"markus@danubetech.com"`.

Using these rules, the above XDI graph can be stored in IPFS as follows:

	# ./ipfs object data QmePRoNxYBM52rX4Lz9uoUEnbzoFJrdcoQFEmn1iU3Gu3N
	{}

	# ./ipfs object links QmePRoNxYBM52rX4Lz9uoUEnbzoFJrdcoQFEmn1iU3Gu3N
	QmPFFA37U3nEHVSqsPwKaW6217kCmhjS7xDPam8f2jh3Gz 0 =markus   
	QmStX2p9x3AV9Gdp1ArLk7bLNzZft5WCBxSLCp4NdbU3z4 0 =drummond 
	
	# ./ipfs object links QmPFFA37U3nEHVSqsPwKaW6217kCmhjS7xDPam8f2jh3Gz
	QmeRY6if7tCE3Ftnk7RVWoq9ohshBm87FS1DM1RvEuyxzt 0 <#email> 
	QmQ6Jwb2uVwBYbaPRwSr61wZYCu6fVS1FX4L2fU4tB9RgW 0 <#tel>   
	
	# ./ipfs object data QmeRY6if7tCE3Ftnk7RVWoq9ohshBm87FS1DM1RvEuyxzt
	{"&":"markus@danubetech.com"}
	
	# ./ipfs object data QmQ6Jwb2uVwBYbaPRwSr61wZYCu6fVS1FX4L2fU4tB9RgW
	{"&":"+43 664 3154848"}

The only remaining question is then how XDI relational arcs can be modeled. Simply modeling them as IPFS links is not possible because of the constraints of the Merkle DAG structure. We explore two options:

**Option #1**: We can model an XDI relational arc as data in the IPFS node corresponding to the XDI context node that is the source of the XDI relational arc.

Using this approach, the XDI relational arc can be stored in IPFS as follows:

	# ./ipfs object data QmPFFA37U3nEHVSqsPwKaW6217kCmhjS7xDPam8f2jh3Gz
	{"/#friend":["=drummond"]}

The downside of this approach is that graphs may become inconsistent, e.g. the XDI context node `=markus` may indicate an XDI relational arc `#friend` to an XDI context node `=drummond`, but this XDI context node may not actually exist in the graph.

**Option #2**: We can model an XDI relational arc as an IPFS node with two IPFS links that point to the IPFS nodes corresponding to the XDI context nodes that are the source and target of the XDI relational arc.

Using this approach, the XDI relational arc can be stored in IPFS as follows:

	# ./ipfs object data Qmebb2jZqQjfTwmhdZsY8nBdb8zs1rHLNRhPL9Kb2kw8Z2
	/#friend
	# ./ipfs object links Qmebb2jZqQjfTwmhdZsY8nBdb8zs1rHLNRhPL9Kb2kw8Z2
	QmPFFA37U3nEHVSqsPwKaW6217kCmhjS7xDPam8f2jh3Gz 0 source 
	QmStX2p9x3AV9Gdp1ArLk7bLNzZft5WCBxSLCp4NdbU3z4 0 target 

The downside of this approach seems to be that is impossible to actually find XDI relational arcs while navigating the graph structure, unless additional overhead such as an index of all XDI relational arcs is introduced.

XDI Peer Roots for IPFS/IPNS
----------------------------

XDI peer roots are used to identify the roots of XDI graphs at their specific locations in a network.

For IPFS, we introduce the following scheme for XDI peer roots:

`($ipfs)(=!:ipfs:QmePRoNxYBM52rX4Lz9uoUEnbzoFJrdcoQFEmn1iU3Gu3N)`

This is an XDI peer root identifying an XDI graph who's root node is stored in IPFS at the node with hash `QmePRoNxYBM52rX4Lz9uoUEnbzoFJrdcoQFEmn1iU3Gu3N`.

Since IPFS uses content-addressing, this XDI peer root would change every time the XDI graph is modified.

This is where IPNS can help, which introduces a mutable mapping to IPFS nodes which are themselves immutable.

For IPNS, we introduce the following scheme for XDI peer roots:

`($ipfs)(=!:ipns:QmX2H9dimN3Bit5Xf2HNyE5TnknPR7bXhxpEUXSgbu2snW)`

This is an XDI peer root that remains constant even when the XDI graph in IPFS is modified.

Motivation
----------

Since XDI is an abstract model for distributed identity, XDI graphs stored in IPFS can seamlessly integrate with XDI graphs stored elsewhere, e.g. graphs at personal clouds endpoints, or data that is not itself natively in XDI format.

For example, Markus could link his e-mail address in his personal cloud to an e-mail address stored in IPFS using the following XDI reference link:

`=markus<#email>/$ref/($ipfs)(=!:ipns:QmX2H9dimN3Bit5Xf2HNyE5TnknPR7bXhxpEUXSgbu2snW)=markus<#email>`

XDI-enabled applications and services trying to discover Markus' e-mail address would now know that they can retrieve it from the distributed IPFS store instead of having to interact with a traditional XDI endpoint.

Implementation
--------------

An experimental Java implementation of this mapping is available at:

https://github.com/projectdanube/xdi2-ipfs
