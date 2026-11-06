---
layout: post
title: "The Hidden Cost of Tiny Dependencies"
date: 2026-04-14 20:46:00 +0000
---

I have been thinking a lot about npm dependencies lately, especially the small ones.

Not the big libraries that solve hard problems, but the tiny packages that do one small thing: strip whitespace, pad a string, check a type, or format something simple.

A good example is [`strip-indent`](https://www.npmjs.com/package/strip-indent), a small package that removes leading whitespace from each line of a string. If you open the source, it is not magic. It is a short function with a regex, a loop, and a replace.

Useful, yes. But also the kind of thing many teams could probably own directly in their own codebase.

---

## The problem with "just install it"

Installing a package became so easy that it often feels easier than creating a small `utils/` file and writing the function ourselves. Need a helper? `npm install`. Need another helper? `npm install`.

After a while, your project has hundreds of packages in the tree, and most people do not really know what half of them do.

A tiny dependency feels harmless. The bundle size does not change much, the build still works, the linter is happy, and nobody complains.

But the real cost is not size.

**The real cost is trust.**

---

## Small code, big trust

Every package you install becomes part of your supply chain. It may run during install, it may run in CI, and it may run with access to your environment, your tokens, your `.env` files, or your build system.

A package that strips whitespace does not need network access. It does not need filesystem access. It does not need to spawn processes.

But npm does not really stop it from doing those things if a future version changes.

That is the part people forget. You are not only trusting the code you see today. You are also trusting:

- Future releases
- Maintainer accounts
- Publishing tokens
- The registry
- Your lockfile
- Your CI setup

For a small helper function, that is a lot of trust.

---

## This is not only about small packages

To be clear, big packages can get compromised too.

[`Axios`](https://www.microsoft.com/en-us/security/blog/2026/04/01/mitigating-the-axios-npm-supply-chain-compromise/) was a good reminder of that. Axios is not a tiny package. It solves a real problem. Most teams do not want to write their own HTTP client because there are many edge cases and a lot of behavior to get right.

So the lesson is not "never use dependencies." That would be silly.

The lesson is that **supply chain risk is real**. And if that risk exists even for large packages, then we should be more careful when adding tiny packages that do very little.

With a big dependency, there is usually a clear reason it exists. With a tiny dependency, the question is different:

> *Are we accepting the same trust risk just to avoid writing a few lines of code?*

---

## The rule I use

When I look at dependencies, I keep the rule simple:

**If the code fits on one screen, has no platform-specific behavior, and has no tricky edge cases, I usually do not want it as a dependency.**

I would rather write it, put it in a `utils/` file, add a small test, and own the code. Yes, now you maintain it. But if the code is ten or fifteen lines, that is not a big burden. At least the audit is simple. You can read it once and understand it.

Save dependencies for things that are actually hard:

- Cryptography
- Parsers
- Date and timezone logic
- HTTP clients
- Framework integrations
- Anything with real standards and painful edge cases

Those are the places where using a package makes sense.

---

## Before you `npm install`

Every dependency is another thing that can change. Another account that can be compromised. Another install script that might run. Another package that nobody reviews during a normal update.

So before adding a tiny dependency, ask one simple question:

> *Is this package doing enough to justify the trust I am giving it?*

If the answer is *no*, maybe it should not be in the tree.

Sometimes the safest dependency is the one you never install.
