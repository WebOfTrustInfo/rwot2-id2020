**Identity Crisis**

**Clearer Identity Through Correlation**

A white paper catalyzed by the ID2020 Design Workshop, May 2016, New York, NY.

**Joe Andrieu, Editor &lt;**[***joe@joeandrieu.com***](mailto:joe@joeandrieu.com)**&gt;**

**Kevin Gannon &lt;**[***kevin.gannon@gmail.com***](mailto:kevingannon@gmail.com)**&gt;**

**Igor Kruiper &lt;**[***ikruiper@ymail.com***](mailto:ikruiper@ymail.com)**&gt;**

**Ajit Tripathi &lt;**[***ajit.tripathi@uk.pwc.com***](mailto:ajit.tripathi@uk.pwc.com)**&gt;**

**Gary Zimmerman &lt;**[***gzimmerman1024@gmail.com***](mailto:gzimmerman1024@gmail.com)**&gt;**

Introduction
------------

We propose using “correlation” instead of “identity” when discussing concrete identities in identity systems. It isn’t a word-for-word replacement, but using it *will* improve the conversation.

For the length of this paper, we ask you to consider, “What if there were a different way to talk about *Identity*?” Take a moment to step outside your current use of that term and look through a different lens. Allow a different take on a well worn term to illuminate your work in a new light.

The term “identity” is a challenge.

Both laypeople and experts struggle to communicate clearly about identity. The term has numerous rich and useful meanings. That same flexibility and expressivity also make it easy to misunderstand subtle nuances. We compensate with adjectives, like “digital identity” or “legal identity”, but often still speak past each other. We regularly refer to “identities” as things either assigned to us or that we own; identities we control or present—instead of using more rigorous terms such as “identifiers” or “credentials”. This fluidity often confuses because, at its core, identity is an emergent phenomenon that doesn’t have an existence independent of the observer.

We argue that “correlation” provides a more concise and clear understanding of how identity is created and used in both digital and real-world systems, and that using it as an alternative to “identity” will improve communication and understanding.

Identity fundamentally depends on correlation
---------------------------------------------

Without an observer to recognize a subject, identity doesn’t exist.

In simpler terms, if identification doesn’t occur, there is no identity.

In this alternative lens we’ve asked you to peer through for a moment, we challenge the appropriateness of focusing on an “identity” as a property of a thing (or person), rather than as a phenomenon that emerges between an observer and a subject. We think that using the phrase “an identity” obfuscates more than it communicates.

We’ve personally experienced thousands of hours of discussion, debate, and disagreement about just what “identity” means. As identity professionals, we understand the need to clarify the lexicon. It’s important. Unfortunately, we keep seeing the same conversations repeated with different highlights and influences in every new community that needs a common understanding of the term.

Fortunately, even with the potentially confusing use of “identity” as a property, all of the varied senses of identity depend on correlation, as we’ll explore next. We use that foundation to propose focusing on correlation instead of identity-as-a-property when discussing identity systems.

Consider three excerpts from dictionary definitions of “identity”.

First, from the **Collins English Dictionary**[1]:

1.  the state of having unique identifying characteristics held by no other person or thing

the individual characteristics by which a person or thing is recognized

Second, the **Unabridged Random House Dictionary**[2]:

1.  the state or fact of remaining the same one or ones, as under varying aspects or conditions:
    > *The identity of the fingerprints on the gun with those on file provided evidence that he was the killer.*

2.  the condition of being oneself or itself, and not another:
    > *He began to doubt his own identity.*

Third, from **Merriam Webster**[3]:

1.  a : sameness of essential or generic character in different instances
    > b : sameness in all that constitutes the objective reality of a thing : oneness

2.  a : the distinguishing character or personality of an individual : individuality
    > b : the relation established by psychological identification

Collins favors identity as a collection of characteristics. Random House focuses on a state of unique continuity. Merriam Webster suggests both.

What all eight senses share is the notion that identity addresses continuity across contexts. Identity means that an entity can be recognized in a later context as, somehow, the same entity known from an earlier context:

-   Two definitions focus on the characteristics that allow this recognition (Collins 1, 2, and Merriam 2a),

-   four focus on sameness (Random House 1, 2 and Merriam 1a, b), and

-   three (Collins 1, 2 and Merriam 2b) focus on the mental act of recognition.

Despite these three different senses of identity (characteristics, sameness, recognition), they all describe relating what is known about a subject in one context to something else known about the same subject in another context. In other words, “identity” means correlating information about the **same** subject in **different** situations. If we can identify a subject, we know something about him or her that isn’t based on immediate observation.

However, when we treat identity as a property, e.g., as “a digital identity”, rather than the emergent phenomenon of identity, we sometimes confuse the conversation. We often refer to the characteristics and credentials we use for recognition as if they constitute identity *independent* of recognition by an observer.

In discussing modern identity systems, professionals and engineers sometimes say:

-   "you select your identity," or

-   "we store the identities in the blockchain," or

-   "users own and assert their own identity."

These statements ignore the role of the observer and often confuse the listener about what is actually selected, stored, and owned & asserted. This conflation of identifiers, attributes, credentials, and identity is, we believe, a primary driver of miscommunication and misunderstanding in identity discussions.

Identity is more than just bits
-------------------------------

Identity manifests when we see a face and recall the name. It is in play when we see a badge and acknowledge someone’s authority. It emerges when we see an individual and treat them as white or black, gay or straight, male or female.

It doesn’t exist without that correlation of identifier or attribute with a subject. If you can’t identify a thing, it means you can’t place it. You can’t relate it to something else you already know. It has no identity, precisely because you can’t correlate it with anything else.

Take an arbitrary string of hexadecimal digits:

#####  190B95B104BD41ACA53D9C1486B26C71

Without further information, we can’t tell if that is an identifier, an attribute, a credential, or just entropy. It may eventually become an identifier, but it isn’t yet, not until someone associates it with the thing it identifies. A randomly generated GUID, like the one above, may or may not ever become an identifier.[4] It’s just an example string of digits. It is certainly not an identity.

Yet, if I were to assign that GUID as an identifier for some object, **everything** changes and it **becomes** an identifier. This is the semiotic nature of the signifier and the signified[5]. Until the string is accepted as, or known to be, a signifier referring to some, potentially as yet unknown, signified, it isn’t an identifier. It’s just a string of hexadecimal digits.

Similarly, any concrete “identity”, such as a collection of attributes in a verified claim, isn’t actually an identity until and unless an observer correlates it with a subject. We may have a username or an email address or a string of UTF8 characters with the label “name”. These bits of information could exist anywhere: in a database, in a form submission, or printed on a piece of paper. They may even occur when millions of monkeys type on a typewriter. We might even know that the data are identifiers rather than arbitrarily ordered bits, but until a specific piece data is associated with a subject, they aren’t an identity. They are, at best, identifiers and, at worst, arbitrary bits.

Consider the password cracking tool Medusa[6]. Like many password crackers, Medusa will accept a file containing strings to use as user names in a brute force attack. Unless the target system actually has a matching login for a given string, that string isn’t an identity in that system (or potentially anywhere, as the strings could be randomly generated). Until the target system correlates that string with the username of an account on the system, it is incorrect to describe that string as an identity. Yet we often refer to usernames as “identities”.

We make that mistake every time we refer to “identities” in isolation from that fundamental act of correlation.

Consider this…

> DNA doesn’t identify a person until it is used to correlate him or her with evidence at a scene of a crime, or links her or him to an ethnic group or ancestral lineage. Without correlation, DNA is simply a physical encoding that drives protein generation in the body.
>
> The social security number for a child, printed on a card, stored in a filing cabinet, isn’t an identity until and unless he, or someone else, uses it. The number itself is just a number.
>
> An “identity” is not the sum collection of all the ways that one might be identified… we can watch any good detective show and see the trail of clues that lead to tracking down a suspect; yet we don’t think of each clue as an “identity”.
>
> Identity isn’t the sum of all of the attributes and actions that might be wrongly or rightly ascribed to you, and may, in one way or another, be used to figure out “who you are”. These are at best a digital profile, at worst the data bloat of a runaway surveillance network.

These are examples where common notions of “identity” lead to incomplete, inaccurate, and confusing interpretations.

The philosophy and politics of identity
---------------------------------------

Typical digital systems use identifiers, attributes, and historical logs to correlate individuals across contexts such as visits to a website. Typical real-world systems issue credentials that bind identifiers to long term, observable, measurable attributes and facts—such as name, race, height, weight, hair color, a picture, and birthdate—in order to correlate a human with certain privileges or responsibilities, like a license to drive.

In discussing both digital and real-world cases, we sometimes confuse the notion of identifying a singular “self”--a specific human person--with the mechanisms by which we do so. This leads to philosophical and civil debates about such things as the right to be forgotten and the innate value of anonymous and pseudonymous speech in a functioning democracy. When we think about “identity” in terms of “who we ***are***”, we get caught up in the consequences and ramifications of policy and privacy and human rights. These are important debates, but they often slip into abstractions, miscommunication, and political disagreements that undermine our efforts to build functioning identity systems. On the other hand, when we think about “identity” as a mere collection of attributes or identifiers, we ignore and sometimes dismiss the deeper meanings others interpret in the word.

We shouldn’t need to resolve our political and philosophical differences to describe an identity system. To champion a particular feature or capability, yes, the more human side of “identity” is absolutely relevant. But to describe and discuss the functional mechanisms of a given identity system, we are better served using concrete, non-political, non-philosophical terms.

In the digital and real-world systems described above, we were able to quickly describe the mechanisms of identity using the term “correlation” without getting sidetracked into more abstract discussions like “What is Legal Identity?”[7] or “Is anonymity possible?”

*That* is the point of this paper.

We argue that, when discussing identity systems, “correlation” enables a more concise discussion and clearer understanding of how identity is created and used[8]. It’s not that “identity” is incorrect, it’s that the mechanisms of identity are inherently mechanisms of correlation and *therefore*, we can be clearer by focusing the discussion how correlation is managed.

Everyone, layperson and expert alike, can be more concise, more rigorous, and better understood by using correlation (*and* anti-correlation) when discussing *the exact same identity systems*.

Illustrations of Identity using Correlation
===========================================

Here are several examples of identity in the modern world. We discuss each using the terminology of correlation. These situations represent a broad range of identity and identification, demonstrating that our proposed focus on correlation applies beyond specific technical implementations or use cases. It can be used to describe identity in any context.

-   **More than a Piggy Bank** *Transitive Correlation*

-   **Beverage Bracele**t *Temporary Correlation With Limited Disclosure*

-   ***He* Did It!** *Correlation Using Neither Identifiers Nor Consent*

-   **I Know Where You Live** *Unwanted Correlation*

-   **Pinkeye Guy** *Spontaneous Correlation*

More than a Piggy Bank
----------------------

###### **T**ransitive Correlation

In the U.S, when we go to the bank to open an account we provide our social security number, in part so that banks can comply with federal regulations, such as reporting cash transactions over $10,000. Banks issue account numbers and record signatures so they can reliably correlate our deposits and withdrawals with our accounts. The social security number is, generally, only used by the bank for regulatory filing. In turn, the government uses our social security numbers to correlate our taxable and fiscally regulated transactions throughout our lifetime.

This is transitive correlation, where an identifier is used not by the immediate recipient for correlating our direct interactions with them, but when the recipient needs to refer to us in communications with a third party. Because of the ready availability of social security numbers and its innate role in reporting personal finances to public agencies, it is *also* often used by financial intermediaries to query and report private financial interactions. Credit bureaus and creditors use social security numbers as a primary identifier to correlate individuals across credit transactions. This unintended use has made the social security number both more valuable and, unfortunately, more accessible, as a target for “identity theft”. Correlation by the US and state governments is the intended correlation. Correlation by creditors and credit bureaus is unintended, and the correlation by identity thieves is undesired.

Beverage Bracelet 
------------------

###### Temporary Correlation with Limited Disclosure

When we attend a music festival, we sometimes receive a disposable, colored bracelet that allows us to purchase alcoholic drinks. To get the bracelet, we provide proof that we are at least the minimum legal drinking age, to a single, designated agent at the event. Then, throughout the grounds, the bracelet allows us to purchase drinks from bartenders without further use of legal credentials. At the point of sale, the bartender can verify that the person ordering a drink has been vetted for the legal age limit by the presence of the bracelet, which can’t be removed without destroying it. These bracelets are durable enough to last for as long as a few days and are generally discarded rather than reused; different events use different colors and patterns so it is a challenge for underage drinkers to know before hand what type of bracelet would let them sneak past the age restriction.

This is an example of a temporary correlation and limited disclosure. The information contained in the bracelet is minimal--”the wearer has demonstrated proof of age.” This limits disclosure of potentially risky personally identifiable information, like birth date or address, to the initial point of issuance[9]. The bartender gets just what they need, just when they need it. Bracelets are an inexpensive, privacy enhancing technology that also reduces the time bartenders spend checking IDs--which increases sales and profit--and reduces the compliance costs for the venue. Not only is it easier to manage than alternative systems, like isolated “beer gardens”, the bracelets themselves provide evidence of due care to authorities who regularly punish non-compliant vendors with penalties from $10,000 up to revoking the liquor license.

*He* Did It!
------------

###### Correlation using neither identifiers nor consent

It is a staple of crime dramas and real-world courtrooms to call on eyewitnesses to literally point out the alleged offender so the jury can see whom they are accusing. Prosecuting attorneys love eyewitnesses because they provide a human face for corroborating the physical evidence. At the same time, defending attorneys will go to great lengths to question the veracity and the character of the witness to undermine their claims. The success of one side or another can literally be a matter of life or death in cases of capital punishment.

The battle before the jury depends on whether or not they believe the asserted correlation. That identification does not depend on the eyewitness knowing the name of the accused, their address, birthdate, or social security number. The eyewitness simply needs to demonstrate that they reliably recognize the accused as the party they saw committing the crime[10]. Yes, eyewitnesses are known to be wrong sometimes, just as forensic evidence is never 100% accurate. The battle is between the prosecutor’s efforts to correlate the accused with the crime and the efforts of both the defense attorney and the accused to prevent that correlation. Criminals often go to great lengths to lay false trails, hide or destroy evidence, and even lie or commit further crimes in their attempt to prevent such correlation. The “identity” of the killer ultimately depends on the court’s ability to fairly and accurately resolve this battle of correlation.

In this example of identity, the subject, i.e., the alleged murderer, does not consent to the correlation. While many valid digital identity use cases base their architecture on consent and control by the subject, that doesn’t apply to all situations. This is especially true for law enforcement, border patrol, and the military[11]. In order to allow regulators, lawmakers, ambassadors, and heads of state to make decisions about digital identity systems, it will be vital to understand how such systems correlate people and how they prevent undesired correlations. The goal is a system that is flexible enough--and *understandable enough*--to allow organizations, companies, and sovereign states to choose the best tradeoffs for their needs.

I know where you live
---------------------

###### Unwanted correlation

In the Jungle of Calais, seven thousand refugees fleeing political strife and violence have forged a temporary home[12]. In nine months it went from virgin ground to the largest slum in Europe. In harsh conditions, many fear any form of identification, knowing that their families back home could be punished or killed by the regime they fled if the link is made between them and those they left behind. The lack of identity credentials makes it hard to access justice and health services and to integrate into society. Their fear of persecution keeps many on the fringe. Some have destroyed identity documentation while others avoid even being recorded for unofficial documentaries.

This is the fear some refugees live with every day. For the regimes, it is identity weaponization; for the refugees, it is fear of unwanted correlation. In this case, the consequences aren’t harms done directly to the subject--the traditional focus of privacy efforts--but rather the harm that might be done to friends and family back home. Unfortunately, this directly conflicts with the approaches of several identity solutions presented at the recent ID2020 Summit and the related ID2020 Design Workshop. One in particular proposed a DNA registry designed to help refugees reconnect with family back home. It will be hard to get refugees to participate in such a program when being connected with family is exactly what they fear.

The challenge is to build a system that allows just-enough correlation, just-in-time, to enable the services necessary for human dignity and freedom, without facilitating unwanted correlation that can and does enable further violence and even genocide. Perhaps the trickiest part will be finding a solution that is so clear and obvious that the typical refugee, despite distrust of formal authority and speaking a second language, can understand it and believe it won’t put their loved ones at risk.

Pinkeye Guy
-----------

###### Spontaneous Correlation

Consider a dinner party where, tragically, a guest who happens to have conjunctivitis (aka pinkeye) trips and breaks the host’s favorite vase. Later, we might not recall his name, or maybe we never knew it. Yet, there’s a good chance we’ll remember that guy who had pinkeye:

> “Remember that guy who smashed Elly’s vase?”
>
> “Who? Oh, you mean Pinkeye Guy?”
>
> “Yeah! I bumped into him the other day at the Royal Oak. Turns out he just published a book.”

In social contexts, we sometimes use a unique feature or distinguishing moment to refer to shared or indirect acquaintances. These spontaneous monikers allow us to refer to the party in question in conversation with others who observed--or sometimes just heard about--the memorable distinction. The nickname may never have been used before and may or may not establish a long term reference, yet when understood by the people we’re speaking with, it allows correlation between the current subject and the referenced individual.

In this spontaneous correlation, the subject has no control and often never even knows about the nickname. The identity is real, useful, and completely emergent.

Conclusion
==========

Using “correlation” to describe identity systems provides a simpler, more coherent view of mechanisms, capabilities, and risks. The term doesn’t change the nature of the system. It is simply more concise and more accurate. It results in discussions that are more rigorous and easier to understand.

Even if you disagree with our arguments about *why* “identity” as a property is problematic, you can still use “correlation” to be clearer.

When you find yourself in a project where the definition of “identity” seems to be a repeating source of challenging conversations, try describing the role of identity in terms of correlation. Shifting to alternative language may help you and your colleagues see the commonalities in your perspectives rather than the differences. It may allow perspectives to be heard that were getting lost in the debate. It may highlight that the issue at hand is more political than technical and allow the group to steer the conversation in the most productive direction, whichever way that is.

We believe that *every* identity system can be fully characterized by how it manages correlation across contexts.

So, please, use “correlation” when you describe identity systems. Use it when you discuss identity systems with both laypeople and experts. Use it when you build, validate, and improve identity systems.

We believe that doing so will make you more effective and more productive, and your resulting systems more successful and more appreciated.

[1] identity. Dictionary.com. Collins English Dictionary - Complete & Unabridged 10th Edition. HarperCollins Publishers. [*http://www.dictionary.com/browse/identity*](http://www.dictionary.com/browse/identity) (accessed: June 09, 2016).

[2] identity. Dictionary.com. Dictionary.com Unabridged. Random House, Inc. [*http://www.dictionary.com/browse/identity*](http://www.dictionary.com/browse/identity) (accessed: June 09, 2016).

[3] "Identity." Merriam-Webster.com. Merriam-Webster, n.d. Web. 9 June 2016.

[4] In this case, it isn’t at the time of this writing.

[5] Review any text on semiotics for further details.

[6] JoMo-Kun, “Medusa Parallel Network Login Auditor”, *foofus.net*. Online. Accessed Jun 14, 2016. [*http://foofus.net/goons/jmk/medusa/medusa.html*](http://foofus.net/goons/jmk/medusa/medusa.html)

[7] The topic of one of the panels at the ID2020 Summit, where, unfortunately, none of the panelists could offer a concise answer.

[8] Note, we did not say “how *identities* are created and used”. That’s the terminology that got us into this mess.

[9] Data typically found on credentials accepted as proof of age, such as a driver’s license or passport

[10] Sometimes the witness didn’t see the actual crime, but saw some other correlating activity, such as leaving the building with a suspicious weapon, etc.

[11] In particular, the 2014 Ottowa Treaty governing the use of indiscriminate antipersonnel land mines requires militaries to “positively identify” all targets. Obviously, this is not a matter where consent is appropriate.

[12] O’hara, Finlay. *Jangala.* May 31, 2016. Video. Online. Accessed June 7, 2016. [*http://theworldwidetribe.com/2016/05/jangala/*](http://theworldwidetribe.com/2016/05/jangala/)
