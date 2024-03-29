---
title: Act IV - All Work and No Play makes XSS
date: 2021-08-10 10:46:53
tags: 
- cybersecurity
- cyber-security
- cyber
- security
- sec
- knowledgezero
- blog
- science
- XSS
- cross-site scripting
---

![](./shining.jpeg)

How long have we been studying the security of these electric sheep? And yet, we're still here in our apartment, "bleeding out digging deeper, just to throw it away". 

*Mom:* Go play outsiiiide! Stop being a nerd and go play with real people! 

*Us:* I don't... 

Wait a second... we live alone in this apartment...  

It's really time to go out before it's too late. Plus, there's a conference on Cybersecurity in town. 

## Yeee, HookLand!  

We walk in and get to the registration desk. A bold guy with his white head is talking with Clerk, the guy at the registration desk. We overhear something like "this process is... and reality has...". Why are they chatting while we wait?! Who cares about registration! We sneak in the conference room and sit in the back. In a few minutes, the first speaker is announced. 

*Chair:* Good afternoon, everyone! It is a pleasure to welcome our first speaker, Professor Patrikal Mann from HaitchIndex University. As you know, he's famous for the discovery of The Firewall technology that we all use to close closed ports and to open opened ports as brilliantly explained in [LifeOverflow](https://youtu.be/fKuqYQdqRIs).

![](./liveoverflow.png)

*Audience:* CLAP! CLAP! CLAP! CLAP! 

*Us:* What the... 

## Presentation title: A few thoughts on XSS. 

*Prof. Mann:* Thanks! After the great success of The Firewall, I decided to illuminate you on another important topic. Today, I'm going to enlighten you on XSS, or Cross-Site Scripting. 

*Audience murmuring:* woooa! Me likey XSS.   

*Prof. Mann:* Cross-Site Scripting refers to a class of security flaws (a.k.a. vulnerabilities) where an attacker can execute *malicious client-side code on a web page by taking advantage of another user's session*. This *means* that when a website is vulnerable to an XSS, an attacker can run some code on your browser!!! 

*Audience murmuring:* Oh no! I won't use browsers anymore! I'll use Internet Exploder instead! 

*Prof. Mann:* Many of you will probably agree on this definition,  

*Us:* Excuse me?! That definition contains important other definitions we don't really know or agree on. What is a "vulnerability"? And what is a "class of vulnerabilities"? You also said: "taking advantage of another user's session", is this necessary?  

*Prof. Mann:* Good observation my young padawan! 10 points to Gryffindor! That is why XSS must be divided into 3 types! 

- Stored XSS 
- Reflected XSS 
- DOM-Based XSS 

*Us:*... but, really... 

*Prof. Mann:* There're, obviously, other very important categories such as self-xss and mXSS, but those categories are too great and complex for this talk. For those of you who dare, [here](https://en.wikipedia.org/wiki/Cross-site_scripting) you can reach the last step of enlightenment as defined by me. 

![](./enlightenment.png)

*Prof. Mann:* Stored XSS happens whenever the malicious client-side code is saved somewhere in the backend and retrieved and executed by a victim user. 

*Us, thinking:* Oh, I see, it's the usual case when you register a new user with name ``<script>alert("storedXSS")</script>`` and then you log-in into a page that "visualizes" your name, opening an alert box! 

*Prof. Mann:* Reflected XSS happens whenever the malicious client-side code is not saved by the web application but is "reflected" within a web page. 

*Us, thinking:* Sure, that's, for example, when I fill in a form searching for ``<script>alert("reflectedXSS")</script>`` and then the page "visualizes" the entry you searched for. 

## Specchio Riflesso chi lo dice sa di esserlo.[*] 
[*]the title "Specchio Riflesso chi lo dice sa di esserlo" is in Italian and refers to a childish mockery like "boing flip" 

![](./specchioriflesso.jpeg)

*Us:* Excuse me?! Why having the malicious client-side code stored or not stored is so important that we categorize XSS into two different categories?

*Chair:* Questions at the end, please! 

*Prof. Mann:* Legitimate question! The answer, according to many, is on how much dangerous one is in comparison with the other. Specifically, Stored XSS is more dangerous than Reflected XSS.  

*Us:* And why is that?  

*Prof. Mann:* Because with Stored XSS, the attacker can store the malicious code directly within the website, without even interacting with the user-victim. This increases the probability that another user of that website will end up executing the malicious code. In the case of a Reflected XSS, on the other hand, the attacker must somehow trick the user/victim into executing the malicious client-side code. 

*Us:* Is this enough to have two different categories? And how did you compute that probability? 

*Prof. Mann:* You are not the only one in this room, let also the other enjoy this talk! So, let you agree with me for the sake of simplicity! And allow me to continue.  Enters DOM-Based XSS! 

*Audience:* CLAP! CLAP! CLAP! 

*Prof. Mann:* To make the matter more interesting, I decided to create a third type of XSS that I called... DOM-Based XSS! What is DOM-Based XSS and why is it different from the other two, you might wonder. Is DOM-Based even more *dangerous* than the other two? 

*Audience:* Lord, no! 

*Prof. Mann:* DOM-Based XSS occurs when the malicious code is never sent to the backend and directly afflicts how the client-side code, loaded when visiting a web site, handles the input supplied by the user. For example, if you inject in a web page something like ``<image search="non-existing-image.jpeg" onerror=alert('XSS'); />`` the image doesn't exist, so the ``onerror`` is triggered. 

*Audience, murmuring:* Genius! Who could imagine injecting code that doesn't even require an interaction with the server! Not even The Firewall can protect you from this! Simply genius! 

*Us:* Excuse me?! 

*Audience, murmuring:* Again?! Shhhh! 

*Us:* Should we wait until you find all possible vulnerabilities in any system by trial and error, or can we jump to the part where you "teach us" how to protect our systems? 

*Prof. Mann:* Sure! SHOWDOWN! Let me present you: *The Web-application Firewall!* It's the greatest discovery after The Firewall! Hold tight! It's a... The Firewall... for Webapps! 

*Audience:*
![](./girl.gif)

*Us:* Excuse me! First, I don't agree with your categorization and, second ...

*Prof. Mann:* Please stop interrupting, come here and "show us" if you have something more than impudence! 

*Audience:* Ugh! We will never get to the coffee break! Where is my free food?! 

## The Ingenious Gentleman of La Mancha 

*Us:* Well... It seems that the malicious code is always retrieved from a user controllable input (which could be the URL bar or a window property) to alter the web page. Why would one of the categories presented be more dangerous than the other? I prepared a sketch of what Prof. Mann said here: 
![](./uml-diagram.jpeg)

*Audience:* What is this? A joke? Where's The Firewall? Nonsense! 

*Us:* In this diagram, you see how to distinguish (and *categorize*) XSS based on the path that the injected code must follows. *Reflected and Stored cannot be distinguished here*. The distinction between those two can be appreciated if we can express causality between events.  

*Audience:* Stop with this ad-hoc models! How do you know that your "models" are a faithful representation of reality!? 

*Us:* My point is that we should not invent metrics based on our experience. We should really stop accepting talks on new useless attacks at HookLand and favour scientific theories instead. Check this out.  

*Us:* Our theory in [here](...) predicts injections as weaknesses. An XSS is just an injection on a specific technology called JavaScript. To reason more universally on XSS, here is a minimal model where the *XSS attack patterns*, mistakenly called "XSS vulnerabilities" by Prof. Mann, can be expressed.  

We take out from our pocket our last sketch. 
![](./scheme.jpeg)

*Prof. Mann:* This really seems ad-hoc! 

*Us:* A model may be high-level but not necessary ad-hoc or un-realistic. When we model a system, we first describe the physical architecture with the physical components, ports and physical channels. In this case: the user (even if he's a Boltzmann brain), the client machine, and the server machine. Like this:  

![](./deployment.png)

*Us:* Then we describe the functional architecture (as before) as a set of interconnected functional elements, that is, without a predefined meaning. The connection between the two views is given by physical ports (present in both models).

*Us:* The functional architecture is "flat" ... as if it were a frame of a movie of an evolving system, so we can analyze the flows only statically. And **statically, the flows are telling us that there exist 2 attack patterns related to the injection weakness in this model**. A dynamic view (of the whole movie-system) would allow us to predict other sub-categories of what Mann called reflected/stored XSS. These attack patterns can be **predicted** by looking at all possible injections points, given a finite model of the system. Summarizing, any system (even a Cyber-Physical electric sheep) is an aggregation of abstract architectures. Architectures come in two flavors (or views), the physical and the functional one; composed by physical channels and ports and functional blocks as building blocks of the behaviour of the system. 

*Prof. Mann:* What I hear is mumbo jumbo! 

*Audience:* Boooooo! Boooo!  
![](./martin.gif)

*Us:* It's a matter of Logic! Of its expressiveness, predicate, first-order, second-... 

## Hey You! Getting Lonely Getting Cold Can You Help Me?
We rushed out of the room... that wasn't a success at all. We should have predicted it! At least we didn't pay... They are also right; models and abstractions cannot be understood by practical men. But we're almost done with the example where we predict vulnerabilities, such as buffer overflows, in C programs. Maybe that will convince them.

We reach the exit and the guy with the white head is coming towards us with Clerk, the guy at the reception desk. 

*White head guy:* You are using my theory, hm?! 

*Clerk:* it's actually mine... I re-wrote your mess in 1981, remember? 

*Us:* Well, I'm using your theories then. They seem to properly predict weaknesses and I'm almost ready to show an application to a piece of C code. But while it works pretty well on static views of a system, it doesn't apply as easily to the dynamics of system interactions. 

*White head:* you know I'm not a computer scientist, right? 

*Clerk:* I see! Did you talk to Saul? 

*Us:* Who?! 

*Clerk:* Saul, the guy from Kripketon. He can help you out with the dynamic part. He can SPINroot your ideas. 

*Us:* Never heard of him, but another guy from another planet... I think his name was Albert or Karl... told me that "I think [...] that theory cannot be fabricated out of the results of observation, but that it can only be invented." while the cleverest tomato thrower of the audience insisted on yelling "[...] your approach is too technical and should instead be rooted in empirical observation and a subsequent creation of theories rooted in those observations". I'm not sure you guys from other worlds are good leaders, you should consider retirement. 

*Clerk:* Nonsense! Let us all meet at your apartment tomorrow at lunch. And, please, take a shower! 

## References 

Alfred North Whitehead was a philosopher and a mathematician [4], and even more. In Whitehead's mess [4], Clarke [5] found logical rigor defining the principles of the Region Connection Calculus, a formal-logical framework for expressing spatial relations between abstract elements of a space (regions, sets, parts, points, ...).  

Kripke's exploration of possible worlds (we suggest [6]) gave us the tools to reason on the dynamics of software [7,8]; engineering processes [9], the methodology to use them. Experiencing the problem of induction [10] in the state-of-the-art cybersecurity technologies [12] made us believe we should try to build new tools based on unexplored theories [13]. 

>When we quantitatively measure [14], 
>artists die [15], 
>and knowledge walks backwards [16].

 
"Upon this first, and in one sense this sole, rule of reason, that in order to learn you must desire to learn, and in so desiring not be satisfied with what you already incline to capably think, there follows one corollary which itself deserves to be inscribed upon every wall of the city of philosophy: Do not block the way of inquiry." [won't cite]. 

  **[1-3]** Hidden  
  **[4]** Editor's preface of Process and Reality -- The Free Press (McMillan publishing): "[S]urely no significant philo­sophical book has appeared in the last two centuries in nearly so deplorable a condition as has this one, with its many hundreds of errors and with over three hundred discrepancies between the American (Macmillan) and the English (Cambridge) editions". Whitehead didn't care too much, and he didn't carefully review the work, even if he was asked to. 
  **[5]** Bowman L. Clarke (Clerk in the story), "A Calculus of Individuals Based on Connection". Notre Dame Journal of Formal Logic, Volume 22, Number 3, 1981. The name Clerk wants to "lower" the importance of Clark's work w.r.t. Whitehead's one (but it really is Clerk 1-0 Whitehead). While Clark‘s work is the standard reference for RCC as a (non-trivial) formalization of Whitehead's work, Whitehead fought far bigger "abyssal monsters" to write "process and reality" (Clerk 1-1 Whitehead). On the other hand, Whitehead messy work loses against (Clerk 2-1 Whitehead) the perfect framework imagined by Clark. In the story, even if a clerk, Clark is the one who "understands" the impractical main character and bluntly exposes Whitehead mess. And a Clerk wins this game against the professor. 
  **[6]** Saul Kripke (Saul from Kripketon in the story), "Naming and Necessity". But you should really be familiar with transition systems, modal logic, Kripke semantics and read Kant's Critique of Pure Reason to grasp the depth of this book.  
  **[7]** SPINroot.com is a model checker where one can abstractly represent software and predict their evolution in time (as a structure representing causality). It is also free and open-source, unlike NuXMV. 
  **[8]** The system models in the story are freestyle UML (Unified Modeling Language) models. Freestyle because we use UML instead of speculating which is the best way of using a semantics-less language. 
  **[9]** ISO 27001, NIST SP 800-53. 
  **[11]** K. Popper, The logic of scientific discovery. In this book, Popper proposes the much-contested idea (see Feyerabend "Against Method" v.1993 for a sometimes mean, always great objection) that a mathematical object should be used to (i) deduce universal laws and then (ii) empirical experiments performed with the objective of falsifying universal laws. In the story, there is a reference to a letter sent by A. Einstein to K. Popper where Einstein agrees with Popper's methodology [17]. 
  **[12]** Firewalls in the story are supposed to be wrongly applied to a decently configured server.  
  **[13]** The root of our work is available at https://www.v-research.it/research.html and the first prototype at https://github.com/v-research/cybersecurity/tree/master/prototypes  
  **[14]** The h-index (haichIndex University in the story refers to this) weights the quality of a professor/researcher/student. It doesn't require a clever person to understand that this is plainly wrong. The weight of a melon doesn't give you an idea of its quality, you've got to smell it!
  **[15]** "yeee, HookLand" refers to the IEEE Security & Privacy (S&P) conference, often called Auckland for historic reasons. The citation "your approach is too technical and should instead be rooted in empirical observation and a subsequent creation of theories rooted in those observations" is part of the brief review we received from one of the S&P reviewers (the cleverest tomato thrower of the audience in the story) and the comparison with what Einstein and Popper believed [17] speaks for itself. It is probably true, nonetheless, that the paper we sent didn't have the quality to be accepted at a conference. You can judge it yourself by reading it [here](https://www.knowledgezero.com/etiology-of-cybersecurity/) and you can maybe give us some meaningful feedback by opening issues or discussion [here on GitHub](https://github.com/v-research/cybersecurity/tree/master/reports/paper_0).
  **[16]** P. Feyerabend, Against Method 1993 edition. The author proposes and justify his view that "[S]cience is an essentially anarchic enterprise". Even if the author rejects Popper's realism ("concepts that are hidden in observation statements are not likely to reveal themselves in the more abstract parts of language. If they do, it will still be difficult to nail them down") he also supports our method: "Theoretical anarchism is […] more likely to encourage progress than its law-and-order alternatives". 
  **[17]** "Albert or Karl" in the story refers to a letter that Albert Einstein wrote to Popper: "[...] and I think (like you, by the way) that theory cannot be fabricated out of the results of observation, but that it can only be invented." -- R. Karl Popper. The Logic of Scientific Discovery. New York London, 1959. 


**End of Act IV.**
