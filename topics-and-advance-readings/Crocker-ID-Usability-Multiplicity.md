## Usability and Multiplicity in Global Identity Management
*D. Crocker ~ dcrocker@bbiw.net*

*Comments for the Rebooting the Web of Trust Discussion ~ May 2016*

We seek a capability that is successfully deployed and used at a global scale, for an extremely diverse population of users and operators, with no single point of control (or failure.)  Arguably there is no service today that satisfies such a set of requirements.  Although the fully decentralized packet-switching mechanisms of the Internet might be claimed as an example, the practical Internet relies at least on the Domain Name System, which very much does have a single point of control, at the top of its registration and operations hierarchies.

The world does not have any single, universal identity management system. It uses multiple systems, even at a global level. We should not assume that this will change, no matter how successful our efforts and no matter how appealing any currently-fashionable technology might seem. Those efforts, therefore, must have the long-term assumption of multiple, alternative identity management systems. Given the nature of technological change, we also must assume that any given component of the system we build may have multiple, alternative forms and instantiations.

This rule of multiplicity extends to the basic challenge of identification attributes. We must not rely on any single vehicle for carriage of encoded attributes, nor even for any single type of attribute.  Users vary in access to technology and they vary in their own economic, educational, physical and cognitive capabilities. In this light, the preference for treating this topic not as a single, statis property, but rather as an identification *process* that correlates attributes is especially well-taken.

While it is relatively easy to design and even deploy an Internet system, it is quite another matter to create one that achieves ready adoption and use by a diverse population, at scale. On the average, systems that succeed pay quite a bit of attention to the nature, needs and preferences of those who are expected to use the system. This means seeking to understand end users and network of (potentially independent) system operators, and to design for them *in place*. That is, a design, which assumes substantial change in end users or operators, is a design that has crippled itself from the start.

A particularly thorough and salient consideration of the usability challenges in deploying an online identity management system for a highly diverse population is in [^Briggs]. The paper highlights a two-factor approach by [^Herzberg] about critical aspects of successful user adoption, distinguishing *hygiene* and *motivation*. Hygiene factors are necessary, but not sufficient. Failure in terms of hygiene factors will cause users to reject the system. By contrast, motivation factors make the system appealing to users. Do these properly and users will *want* to adopt and use the system.

We must design a system that first carefully attends to the realities of a massively diverse and fully global population of  users. In this light, clever technology is necessary, but its public face must be minimal.



[^Briggs]: [An Inclusive, Value Sensitive Design Perspective on Future Identity Technologies](http://dl.acm.org/citation.cfm?id=2778972&dl=ACM&coll=DL&CFID=784531491&CFTOKEN=52935076)
[^Herzberg]: Frederick Herzberg. 1966. Work and the Nature of Man. World, Cleveland, OH.
