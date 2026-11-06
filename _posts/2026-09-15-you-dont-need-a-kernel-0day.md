---
layout: post
title: "You don’t need a kernel 0day"
date: 2026-09-15 11:04:00 +0000
---

I’ve been in security engineering for more than ten years, and I’m still learning from others. There are some incredibly smart people in this field. If you stay humble, there’s always someone who can teach you something.

One thing I think we sometimes overlook is _how much an attacker can achieve by earning someone’s trust_.

When people imagine a sophisticated attack, they often picture someone digging through code, hunting for a kernel 0day, or studying a company’s infrastructure. Sometimes, a _convincing_ request is enough.

Take the recent Revolut incident. [Revolut confirmed](https://www.theregister.com/cyber-crime/2026/09/14/revolut-falls-for-fake-government-requests-hands-over-customer-data/5296118) that an attacker used an email address on a legitimate government agency domain to submit fraudulent requests for information. The company handed over sensitive customer data in response.

Impersonating a trusted entity is one example. But there’s another scenario I keep thinking about: an attacker running a business with a service people actually want to use.

Imagine a product that works, solves a problem, and gives people a reason to come back. Users sign up, connect their accounts, and share information. Meanwhile, the person behind it could be collecting that data and access for a very different purpose.

The growth of AI tools makes me think about this even more. People connect accounts, set up MCP servers, and approve permissions because they want to finish a task. In that moment, getting the result can feel more important than understanding what they just allowed.

This can happen inside companies, too. Someone finds a useful tool, connects their work account, and recommends it to colleagues. You might say, “But they’re an established company. They have a SOC 2 Type II report .. etc” For me, that’s a starting point. Simply knowing they have those certs is a low bar for deciding whether to trust them with sensitive data.

I want to understand what happens inside and ask the difficult questions. Can engineers read customer data while debugging? Who approves that access, when does it expire, and who reviews what they do? Does sensitive information end up in logs that a much wider team can access? .. and and. These are things I want evidence for before I feel comfortable connecting anything sensitive.

Then there’s the question of intent. Even if the company has good intentions, what happens if an employee decides to share data or sell access to an outside attacker for money? What would prevent that, how would anyone notice, and how much damage could that person do? A company’s reputation and audit report matter, but I still want clear answers about the people who can reach my data.

An attacker willing to build that trust might spend months, or even years, doing it. By the time they ask for something sensitive, the relationship may feel familiar enough that the request barely gets questioned.

I think a patient attacker with a convincing story can be just as dangerous as someone with a serious technical vulnerability. That kind of creativity deserves more attention in security.

We spend a lot of time asking how someone could break into our systems. We should also ask _what would convince us to give them access ourselves._
