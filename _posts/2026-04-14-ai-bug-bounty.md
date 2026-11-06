---
layout: post
title: "AI in Bug Bounty - Thinking First Prompting Second"
date: 2026-04-14 07:07:00 +0000
---

I have been doing bug bounty since 2013. Back then, everything was manual. I used to write my exploits line by line, document every step, and build reports from scratch. It was not easy, and honestly, I did not enjoy writing reports, especially the complex ones. You had to simplify everything clearly to avoid endless back-and-forth during triage.

I have also been on the other side, managing bug bounty programs at companies I worked for. It was easy to tell who was serious and who was not. And to be honest, I learned a lot from good reports. People from all over the world come up with very creative approaches.

Now things are changing fast with AI.

Skilled security engineers are becoming much more productive. AI helps a lot with code review, searching across different sources, and spotting patterns that lead to interesting vulnerabilities. But this only works well because they already understand what they are doing. They know what to ask, and how to ask it.

Even report writing has become easier. You provide context, and you get a clean, structured report. You can refine it, simplify it, and make it easier for triage teams to understand.

But there is another side to this.

I am starting to see people relying too much on AI. Instead of thinking, they expect the model to do everything for them. There is a clear lack of fundamentals, especially among newcomers. And those fundamentals are exactly what you need to write a good prompt.

For example, this kind of prompt is weak:

> “Here is a file. Find me a critical vulnerability.”

Compare that to something like this:

> This code is part of an authorization flow in a multi-tenant application.  
> Assume an attacker is an authenticated user trying to access or modify another user’s data.
>
> Analyze the code for:
> - Missing resource ownership checks
> - Trust in client-controlled input such as user IDs
> - Horizontal or vertical privilege escalation

The difference is clear. In the second case, you bring your understanding of security into the prompt. You guide the model instead of expecting it to guess.

On the program side, I still manage bug bounty programs, and the amount of low-quality reports is growing fast. Many people are spamming with things like missing headers, calling them critical without any real impact, and expecting rewards. When rejected, they get frustrated.

We see the same trend in open source projects with random pull requests that do not add real value.

Because of this, filtering becomes necessary. You need to raise the bar. Not every report should even reach the triage stage.

I do believe AI has a lot of value in this field. The potential is real, and we are only getting started. But along with that, there will be more noise.

Do not get distracted by headlines saying everything is changing overnight. We will still need engineers. We will still need people who understand systems, think critically, and use these tools properly.

Keep learning. Stay curious. Be creative. And enjoy the ride.
