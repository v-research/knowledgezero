---
title: Act III - The Etiology of Cybersecurity
date: 2021-03-01
tags: 
- etiology
- cybersecurity
- cyber-security
- cyber
- security
- sec
- mereotopology
- mereology
- knowledgezero
- blog
- science
- practical-man
- philosophy
---

> Whoever delights in a speculative life and has but moderate wishes, finds in the approval of an enlightened and competent judge a powerful incentive to studies the benefit of which are great but remote, and therefore entirely misjudged by vulgar eyes. 
> To such a judge and to his gracious attention I now dedicate this work […]

Immanuel Kant, March 1781

We publish a first incomplete attempt to identify an abstract law behind the security of systems. Such law is intended to explain security by predicting insecurities in abstractions (or models) of systems, requiring a still missing (but postulated) realization of a cybersecure system. The cybersecurity of a system is often defined as the adherence to some cybersecurity requirements such as confidentiality or authenticity. That such properties improve the security of a system (i.e. if those properties are necessary) is not something we are discussing in this paper. What we argue is that even the very protocols or algorithms introduced in a system to guarantee cybersecurity properties, can themselves be flawed making the whole system insecure. We conjecture that this is an indication that cybersecurity should not be searched in such properties, but rather in an idea explaining why security flaws occur independently from the properties supposedly guaranteed by security requirements, algorithms, protocols, or (sub-)systems. **This makes cybersecurity not an object to be defined but a concept to be understood**. 

Observations show that systems are insecure because systems’ behaviors are not fully foreseen (e.g., at design time). These flaws are errors, which are not generated by a malicious attacker but intrinsic to the system. An attacker (or a pentester) exposes such errors, but errors are necessarily introduced by the ignorance (or wrongdoing) during the engineering process of a system. We propose a formal interpretation of the design of a system, showing how to calculate **all** possible divergences from the intended behavior at a very high level of abstraction (and universality). We are refining and testing our hypothesis at lower abstractions, closer to the implementation code, to understand if our ideas can be used to generate attacks in the logic of protocols and algorithms. 

[The Etiology of Cybersecurity](https://github.com/v-research/cybersecurity/tree/master/reports/paper_0) 
