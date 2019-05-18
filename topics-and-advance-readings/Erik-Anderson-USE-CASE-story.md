Erik Anderson
Bloomberg

For the purpose of this document lets replace Blockchain with DLT (Distributed Ledger Technology). DLT is:
  - A ledger that generally runs in a hostile environment like the public internet
  - It uses cryptography to try and solve identity and ownership problems in this public environment
  - It uses cryptography to try and automate business processes & reduce latency to accelerate the value of money
  - Assets are on and managed on the ledger. Off ledger interactions are considered legacy, slow, and inefficient.
  - Most real use cases of this technology are theoretical discussions, unimplemented, without a single live use case with enough scalability, security, or appropriate regulatory framework in place.
  - There is no privacy, all transactions are on this public ledger and all parties can see those transactions.
  - DLT is the technology not the actual asset. The asset is the application utilizing the DLT (Stock trades, payments, swap trade, currencies, bonds & coupons, etc).
  - Transactions are absolute, there is no reverting the transaction. Chargebacks/returns are a business process because the ledger cannot be reversed. You must initiate a transaction back to the originating party.
  - Current DLT Identity & Data security mechanisms is 'relatively unused' cryptography built for financial services in 1990's. These mathematics has a certain lifetime because computers and distributed calculations are getting faster & more efficient. The current cryptography is not resistive to quantum computer attacks, 5-10yr max additional lifetime, target window 2021-2026.

DLT will eventually become a means to alter existing financial services infrastructure, but not by itself. DLT is missing the same 3 critical puzzle pieces that has plagued all open networks like the Internet: Identity & Data Protection & Legal Insight.
  - Identity:
    - Cryptography is very abstract, hard for users to why & how to securely protect their encryption keys.
    - Simple access to Public key: 1BoJiyRnCN5E2FEG3gbC85d6h3c7Xmcqs1 discloses every transaction performed under that identity
    - Theft of Private: 5KgEvEvubwVJGjVBr8UZPe73kksTLk2dqVXh3JavzGaaJSQBUk4 allows thieves to steal the assets protected by that mathematical identifier.
    - Its a public ledger. Its designed to allow financial inclusion by the 780 million without access to established financial services (unbanked, underbanked, and unbankable). Interestingly enough these individuals don't have the capacity to deal in cryptographic assets but they all have mobile phones. Ideally it allows 'transparency' & 'equality' among network participants.
  - Data protection:
    - Data is written to DLT. There is no confidentiality as everyone can see it. Even if you encrypt the private metadata how do you allow differential access to a pyramid of sensitive/private information.
    - Other data, such as HIPAA, has a 125 year storage requirement and existing data security mechanisms cant achieve this requirement since computer capabilities double every 2 years.
    - Data is exposed to a hostile environment (the internet). Any hacker can download the information and attack the data structures directly. This further challenges security measures around data confidentiality half-life. 5 half-lives is an industry acceptable mechanism to measure the time it takes for data, disclosed publically, to be out dated & useless.
    - Encrypting data breaks existing tools used to measure economic health & statistics. Example: International movement of money, trade flow, imports/exports, etc.
    - Cryptography, like any technology, gets better and changes over time. Existing DLT cryptography is directly soldered/fused into the DLT protocols. This will be very costly, require lots of maintenance and developer time.
    - Blockchain was built with US 'standard' data encryption. No foreign nation trusts the other nations encryption and certainly no one trusts encryption the NSA 'helped develop and recommends'. China, UK, Europe, Japan all have their own deviations of that math and refuse to trust other nations recommendations.
      - Because of this reason its impossible to get consensus on an international data security algorithm. You must use a 'standard' data security schema that allows choices of which algorithms to use. Call this an international schema that wraps local/domestic requirements. Standard good practice engineering approaches can allow interoperability even when absolute math doesn't.
      - This schema also allows new advancements in cryptography to be added to the schema, accounting for advancements in math & technology, without breaking data encrypted through older versions of the schema.
      - Encryption algorithms 
      - Recommended algorithms to support:
        - Block Ciphers: AES,ARIA,CAMELLIA,SEED,TDES,BLOWFISH,XTEA
        - Modes: ECB,CBC,CFB8,CFBfull,OFB,CTR,CMAC,CCM,GCM,XTS
        - Digests: MD5,SHA1,SHA224/256/384/512,SHA3-224/256/384/512/RIPE-MD160
        - Asymmetric:
          - RSA 1024/2048/3072, Diffie-Hellman 1024/2048/3072
          - DSA 1024/2048/3072,EC-CDH P256/P384/P521,ECDSA P256/P384/P521 (Non-standard NIST elliptical curves and coefficients should also be supported)
        - Random Number: FIPS 186-3 A.1.1.2,FIPS 186-3 A.1.2.1,FIPS 186-3 B.3.3,FIPS 186-3 B.3.4,FIPS 186-3 B.3.5,FIPS 186-3 B.3.6, X9.31
        - Key Agree/Transport: RSASVE,RSA-OAEP,RSA-KEM_KAS,RSA-KAS1,RSA-KAS2,KTS-OAEP,KTS-KEM-KWS,KAS
        - Signature Types: RSA-X9.31,RSA-PKCS,RSA-PSS,DSA,ECDSA
    - In essence, the current financial systems reach consensus by reconciliation. This requires a lot of data collection, recording, auditing, processing, and reconciling of vast amounts of information. This process is slow, expensive, and difficult to automate. Existing Blockchain (token based ledger business model) is not a ledger to store enormous amounts of sensitive information with varying privacy, reporting, regulation & access control requirements.
  - Legality/Regulatory:
    - Requires movement of, or linking to, identity. P.e.r.i.o.d.
    - While DLT applications, like Bitcoin, aren't illegal they do challenge, if not bypass, existing KYL/AML, compliance, and regulatory controls.
      - Creates more challenging issues surrounding non-repudiation. It wasn't me because some hacker stole my digital key.
        - Malware Use Case: What if Grandpa's computer is infected with malware, which steals his private key? Are we going to hold him responsible for anything signed by that malware -- even if it means he loses his house? That'd be ridiculous. In particular, an easy way to repudiate is simply to claim "my private key must have been leaked/stolen".
          - Similar remarks can be made about social engineering. When social engineering attacks have a good chance of being successful at stealing the private key, and when the scheme is designed in such a way that ordinary people cannot use it securely, and when the designers know (or should have known) this, I think it is questionable whether jurors will be willing to hold Grandpa responsible, simply because he got screwed by a poorly-designed security system.
        - Humans vs. computers Use Case: Legally, non-repudiation is about the actions of a human. A court is going to be looking for evidence that a human (e.g., Grandpa) assented to the terms of the contract/transaction. The cryptographic schemes cannot achieve that. They can only show that some computer performed some action. Cryptographers like to assume that the computer acts as an agent of the human and the computer's actions can stand in for the human's actions, but this is not a reasonable assumption. For example, malware on the person's computer can apply the private key without the human's consent.
        - Basically, most of the cryptographic research into non-repudiation schemes has the wrong threat model. It is based on assumptions that we've since discovered are faulty.
      - Interestingly if you combine identity and data security but further utilize cryptography for event sequencing you can enforce business processes to be strictly adhered to. Business processes, if codified, cant be skipped because the mathematical steps & sequences wont unlock.

Financial Institutions are faced with much higher regulatory, compliance costs as well as strict restrictions around capital exposure. These institutions are looking for innovative ways to reduce future regulatory and compliance costs as well as optimally manage their existing capital to generate new revenue streams.

In order for DLT to meet those expectations, other problems must be solved. Solving Identity Management, Data Security, and regulatory controls has massive upside throughout all of financial services, DLT or not.

Meanwhile, the short-term business imperatives of current Blockchain-focused FinTech start-ups are directed purely toward developing a single use case for the technology that solves one particular element of the overall puzzle. Mainstream capital markets industry is eager to adopt the Blockchain as a new piece of technology that is both disruptive and empowering, but there is, at present, a misalignment of imperatives between what the Blockchain offers today, and what it needs to offer tomorrow.

To address the above needs we must solve 2 requirements. These requirements are part of 'what Blockchain needs to offer but doesn't and are in no way isolated to Blockchain. As a matter of fact, solving these 2 requirements opens a whole realm of possibilities that were, until now, historically unsolvable. NOTE: This has been attempted utilizing 1990's technology but that failed for reasons like privacy, scalability, performance, isolated approaches, and BIG brains working on small problems.
  - Privacy friendly Identity Management:
    - Usage of Identity in a hostile environment that is forensically trackable yet private at the same time. It needs to allow:
      - Friendly regulatory & legal tracking
      - Utilize anti-snooping measures to protect the privacy of the corporations & individual alike.
      - Extreme privacy for purchases of pharmaceuticals.
    - Empower Government use cases like:
      - Government programs like food stamps and Medicare where the government is providing the funding.
      - Grants. So how were those funds utilized?
	  - Permissioned Government Oversight and regulation without building independent systems
    - Empower business use cases like:
      - Business processes for a shared role or delegable usage in instances of vacations,
      - Incase of death's, willable/transferable assets that were bound to the identity of the deceased.
	  - Role based permissions tied to identity.
	    Example: Bank handlers of corporate dept can be delegated authority to pay vendor invoices for their client immediately to win the highest NET discount.
    - Empower individual use cases like:
      - willable/transferable assets that were bound to the identity of the deceased.
      - Persona's and pure merit based identities and scoring mechanisms for online purchases. When Objective measurements of reliability is bound to a person, the merit becomes far more valuable than the drivers license.
    - 
  - Secure yet configurable access to varying levels of sensitive data.
    - Usage of secure objects:
      - Secure objects allow the access controls for its contents to be integrated with the object. Regardless of where the object is stored, how it is transported, the data is secure.
      - Secure objects have access control mechanisms where in roles can be granted to view various different levels of the objects contents.
	  - Identity is interweaved throughout the objects such that those identities are custodians of the objects information.
    - Secure Objects permissioned by an organization chart and employee roles.
       - Objects are always secure. Even internal employees go through the same permissioning system as 2nd & 3rd parties.
    - There is no back door, only an algorithmic construction for keys to the front door.
      - The front door can be permissioned for roles like State Taxes, Auditors, Law Enforcement, various tiers of regulators, compliance officers, etc.
      - Algorithms construct dynamic Keys for access through the front door.
      - There is a different key for each object. Hacking 1 object only exposes the contents of that singular object:
          Example: Hacking the 1 object only exposes one transaction, not an series/history of transactions.
    - Malware:
      - What if Grandpa's computer is infected with malware, which steals his private key? Malware on the person's computer can apply the private key without the human's consent.


*********************************
Direct Financial Services beneficiaries of Identity/Credentials/Verifiable assets
  - Directly lending
    - Middle market direct lending
    - End consumer direct lending
    - Crowd source lending
  - Insurance
    - Claims:
      - Claims will require verifiable assets tied back to identity & proof of purchases
    - Codifying Contracts (ie Smart Contracts)
      - Financial Services is expecting Smart Contracts to be a container for the execution of financial business transactions. These containers need stronger security and identity to assure all parties are known, trusted.
      - Existing business models can be coded into SmartContracts to accelerate the value of money.
  - Legacy financial services
    - Securely embeddable Identity elements in ISO 20022, FpML, FIX, ISO 8583, etc
  - Trades
    - Real-time valuation of assets and settlement
    - Scoring, ranking, trustworthiness, and other compliant-obligatory algorithms to categorize 'codes of conduct'. This applies to organizations and individuals.
        Even if Settlement occurs real-time, collateral still moves at a future date. We still need to score trustworthiness and bind that identities.
    - Posting of collateral for OTC trades. The posting of collateral & verified assets needs to be tied back to real world identities. Currently 3rd parties (ie clearing houses) are required as part of this step to validate real world ID and asset ownerships. Without DLT+Identity+VerifyableAssets it will be impossible to construct consensus algorithms to facilitate real-time settlement and measure trustworthiness.
  - As a utility to servicing of other Instruments
    - Verifiable assets, by themselves, aren’t as valuable as the channels they create for servicing of other instruments.
      - Corporate actions
      - Bond coupons
      - Dividens
      - Corporate Debt
	    - Shared ledger so that bank handlers of corporate dept can pay vendor invoices for their client immediately, win the highest NET discount, immediately client notification & validation that the invoice was executed and paid.
      - Syndicated loans
      - Private securities
      - Asset back instruments
    - Many financial instruments are asset backed. The algorithmic version of "hard linking of the verified assets to the instruments/securities" and placing on a DLT will allow automation reconciliation of the accounts and instrument repricing.
      - This will add a strong level of operational resiliency to capital markets utilizing asset linking to other instruments.
    - Issuing FIGI codes (Financial Instrument Global Identifier) for assets and tying those to identities will create a forensic trail to help prevent the same asset from fraudulently used for multiple different instruments & business deals.
         Example: 2x, 3x, 4x... over collateralization of the same asset for multiple business deals.
    - A common data encapsulation around which:
      - Financial institutions can use to help settle transactions.
      - Common data structure for embedding of KYC/AML and other compliance information.
      - Data exchange across dissimilar non-interoperable technology.
      - Digitization of analog documentation.
  - Lifecycle management
     - TODO. I know cryptography can be used to enforce lifecycles. However lifecycles in financial instruments are based on time or external events. Need more ideas here.
  - Payments and Remittance
    - Transactions can occur directly between two parties on a frictionless P2P basis. The technology’s application for overseas transactions has the potential to reduce risk, transaction costs and to improve speed, efficiency and transparency.
      - By including identity (either tokenized or privacy protection layer) we can allow regulatory controls over the movement of the value.
  - Issuance, Ownership and Transfer of Financial Instruments
    - A DLT securities market allows traders to buy or sell stocks directly on exchanges or directly to other market participants in a P2P manner without the intermediation services provided by a broker or clearinghouse.
      - By including identity (either tokenized or privacy protection layer) we can allow regulatory controls over the movement of the value.
      - In financial services, chains of custody of a financial instrument is deeply regulated territory. This chain of custody is a very costly legacy process. The only way to speed this up is to securely & privately embed chains of identity/ownership into the very process.
      - Without proper Identity it will be possible for bad actors to continue to create the same chaos thats occurring today. You will need to be securely authenticated with the system and have the proper access controls to the information.
      - Massive privacy issues related to publicizing transaction information over a public network/ledger. As a result of this problem the majority of the capital market industry is focused on development of private/permissioned DLT that will never allow an Internet based browser access to these private networks. Access will likely occur via proprietary applications or proprietary+embedded Webkit technology.
      - By linking credentials to individuals, individuals and assets to corporate entities we can create unique cryptographic identification tagging to tradable instruments. Wrapped within a permissioned based privacy friendly security layer it will allow association of people and assets within a hostile environment (such as a public blockchain running on the internet). This will allow authorized parties to utilize mathematical forensics to trace the chains of ownership yet prevent regulatory snooping.
        NOTE: Some will argue that this is a only on-ledger work effort but even ledger work requires on-ramp, off-ramp, data updates, and linked data to off ledger sources.
  - Clearing and Settlement
    - On the distributed ledger technology (DLT), the entire lifecycle of a trade – including its execution, clearing and settlement – can occur at trade level, lowering post-trade latency and reducing counterparty exposures.
      - This can only occure if the transactions themselves are tied back to real world identities yet layered with security mechanisms that protect the privacy yet allow role based regulatory insight into the transactions themselves. Roles could be State Taxes, court auditors, FinCEN.
  - Servicing of Instruments
    - Through the utilization of smart contracts, financial instruments can be pre-programmed to carry out corporate actions, such as payment of bond coupons or dividends.
      - This is only possible by removing the 20 year old security technologies that current Blockchain was built on and layer on Identity with privacy protective mechanisms.
  - Reconciliation
    - Since DLT is replicated and synchronized database of transactions distributed across a network of users, manual reconciliation become redundant.
      - Identity and security layering will be required that trust (ie access to manipulate underlying assets), is granted only to bits of contacts/ledgers that need to interoperate
  - Know-your-client and Anti-money Laundering Registries
    - the perception of anonymity associated with permissionless DLT like Bitcoin challenges existing know-your-client (KYC) rules and protocols;
    - An individual’s or an entity’s identity can be stored in an Identity Provider and utilized on the blockchain, ensuring secure and rapid ID authentication without the warehousing of sensitive data at third-party repositories. This will allow KYC/AML information to be directly propagated via DLT yet still protect the privacy of the individual
  - Regulatory Reporting
    - The DLT is fundamentally a record of transaction history, delivering a fully transparent, accessible transactional database for governing bodies.
      - By combining Identity & secure privacy layering mechanisms you can grant access to governing bodies without allowing regulatory snooping.
  - Reputational Management System
    - Reputation systems are in dire need of connectivity to real & merit based identities. This will prevent merit based identities (Ebay profile) from being stolen and used by unauthorized users.
  - Fines
    - Since the 2008 financial crisis, twenty of the world’s largest banks including JPMorgan, Citibank and HSBC have paid over US$235 billion in fines. Interestingly, the majority of the fines derived from the banking system’s inefficiency and failure to keep track of "verifiable assets". Example: sold mortgages, insurance products, collateralized assets, etc
    - A lower level standard that addresses verifiable assets, transference of assets, assets chained with other assets, assets with shared ownership, assets with "collateral burdens" will help facilitate creation of a document ledger of assets to reduce the regulatory arbitrage that Financial Services is experiencing.
  - WORDS OF WARNING:
    - 2015 saw a double increase in hacks targeting financial data
    - The very data structures of asset storage & messaging will be targeted by hackers. Direct browser integration of verifiable asset messages is !OUT OF SCOPE! for the time being.
      - Its inevitable that financial asset information starts to move over the public internet
        - As asset information is exchanged it should not be possible to take the information about that asset out of the context for which that information was being exchanged.
          Example: I have a Bar of Gold with QR code xxx, verified/signed by Well Fargo as safely secure in their facility, being exchanged as an asset/collateral for a transaction. Assuming a hacker somehow became a man-in-the-middle of the message chorography and has access to the raw signed asset message, he should not be able to separate that signed asset for a different intent.
        - Verifiable asset exchange information must be 1x1 bound to the parties and inseparable from its original intent.

*********************************
Requirements:
  - Non-repudiable shared ledger for single source of truth for that issued identity
    - Any identity, once issued, cannot be changed by any party, and no parties can make copies of that identity
	- All stakeholders should have direct access to the share repository of identity management yet permission controls prevent 'unauthorized' violation of privacy
  - Secure, tamperproof identity
    - Impossible to take the individual attributes out of the public identity usage and use for unintended purposes.
	- Any credential (or attribute), once bound into the creation chain of that identity, is deemed infeasible to reverse the chain to extract/hijack the raw attribute and use for unintended purposes.
  - Private, unlinkble identity per each usage
    - Each identity is of singular use for 1 transaction.
	- Walking the forensic of the usage of that identity requires permission elevation from the owner(s) of that identity.
  - Longevity:
    - Able to meet 25 year half-life requirements (5x25 for a 125 year total life storage requirement)
	- Resiliant to the effects of quantum computing attacks on the end identity key outputs
  - Permission controls:
    - Allowable confidential sharing of:
	  - Individual attributes of identity (aka a credential)
	    Example: Diploma, Financial Accreditation, Driver's License Number
	  - Verifiable attributes such as a address, over the age of 21
	  - Any attribute, once shared, is 3 way bound between the owning party, verifying party, and the receiving shared party to whom it was shared. It must be impractical for any of the 3 parties to reuse the attribute outside the context of what it was shared for.
  - Auditable:
    - Can prove ownership of the identity
	- Its noted, certain conditions exist to allow Regulatory auditing of the identity usage without empowering regulatory snooping nor penetration of the privacy veil. Essentially this means a Regulator may see that Erik Anderson performed a transaction on this date but they dont have permissions to view the underlying transactions metadata.
	- There exists, certain anonymous attributes, that can be publically shared. This is necessary for development of statistics. Example: Trade flows, economic health, etc.
  - Malware:
    - What if Grandpa's computer is infected with malware? Key management is the hard problem to solve.
      - Keys should be stored on an external device that doesnt have online connectivity?
      - Keys can be stored in a "secure element" that can only be electronically unlocked by grandpa.
