---
layout: post
title: Juniper's Dual EC Incident
subtitle: and what it means
---

This week we released a preprint of our research paper, ["A Systematic Analysis
of the Juniper Dual EC Incident"](http://dualec.org/DualECJuniper-draft.pdf).
The technical details are in the paper, but the short version is this:

Juniper's ScreenOS line of VPN boxes included a random number generator (RNG)
design that looks and behaves very much like a backdoor. This design depends on
Dual EC, an RNG designed by the NSA with a fatal flaw: if someone has the
ability to decide the curve constant Q used in Dual EC, they can potentially
predict all future outputs of the generator.  Despite Juniper's claims
otherwise, their RNG construction exposes this flaw.  This ability to predict
values results in full VPN decryption capabilities for that adversary.

Additionally, at some point after this design was created, an unknown third
party modified Juniper's codebase to include a different value of Q. This value
was presumably selected by this third party attacker, granting them this VPN
decryption ability for all ScreenOS boxes.

To be clear, we have no way of knowing how either of these Q values were
generated. In fact, its entirely possible that both values of Q were selected in
secure ways and the third party attacker changed the value just for fun. I find
that unlikely, and so I see two possible scenarios for how these Q values were
selected. In both scenarios, I assume that the third party Q value is malicious;
otherwise, why go to the effort of changing it? Then, either:

  - Juniper intentionally designed and implemented a Dual EC backdoor and
  selected Q as such,

-or-
{: .center}

  - Juniper generated Q safely and the backdoor-like behavior is an unfortunate
  cascade of unintended bugs and design decisions

<!--more-->

### The Intentional Case

For a moment, lets discuss this as if the first point were true; as if this
were an intentional backdoor. This construction, and ones like it, actually look
like the kind of backdoor that the FBI and Congress are currently arguing for.
Encryption is allowed, but the FBI (or another government agency) would be the
one to select the Q value such that they have exceptional access as needed. In
that case, this makes a great case study to inform the encryption backdoor
debate.

This example is exactly why security and cryptography experts around the
world are saying that crypto backdoors cannot be implemented safely. Here we
have an exceptional access backdoor that was subverted by a third party attacker
without Juniper's knowledge for an extended period of time. The same mechanisms
that allowed the intended party to decrypt VPN traffic equally allowed an
unintended and, in this case, unknown party to do the same. If such a capability
exists, others will find a way to use it.

### The Accidental Case

But what if the backdoor-like behavior of the ScreenOS RNG was unintentional?
What if Juniper intended to create a safe VPN encryption system, but, through a
series of bugs and unfortunate design decisions, created an exploitable RNG?

In that case, I think we have an even stronger argument against exceptional
access crypto backdoors. Designing and implementing a cryptosystem with a
single-party backdoor is more difficult that designing one without one. If we
believe that Juniper was trying to create a secure system without a backdoor,
and we know that they failed to do so, how can we expect them or anyone else to
accomplish the more difficult task of implementing a limited-access backdoor?


### tl;dr:

In either case, the Juniper Dual EC Incident is a strong argument against the
kind of crypto backdoors being advocated by the FBI and the Burr-Feinstein
bill. Crypto is difficult to design and implement correctly, even without
exceptional access backdoors. And with them, we lose security guarantees and can
unintentionally grant adversaries capabilities they didn't otherwise have.
