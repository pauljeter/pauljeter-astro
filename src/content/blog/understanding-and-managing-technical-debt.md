---
title: "Understanding and Managing Technical Debt"
description: "How I think about technical debt: where it comes from, when it matters, and what works to keep it from owning your roadmap."
pubDate: "2022-02-21"
heroImage: "/images/technical-debt.jpg"
category: "Software Engineering"
tags: ["Technical Debt", "Software Engineering", "Best Practices", "Leadership"]
---

Every team I've worked with has had tech debt. Some carried it well. Some let it grow until shipping anything new felt like wading through wet concrete.

There's a stat that gets thrown around, something like $85 billion a year spent globally on refactoring bad code. I don't know how anyone arrives at that number, but it sounds about right when you think about how much of an engineer's day disappears into "fixing the thing before fixing the thing."

So let's talk about it.

### What it is

The financial metaphor is overused but it's useful: you took a shortcut, and you're paying interest on it until somebody refactors. The interest shows up as slower changes, more bugs, more onboarding pain, and more meetings about why a "small" feature is taking three weeks.

A useful way to slice it:

- **Deliberate vs. unintentional.** Deliberate is "we know this is the wrong abstraction but we need to ship by Friday." Unintentional is "we didn't realize this was the wrong abstraction until it bit us six months later."
- **Reckless vs. prudent.** Prudent debt means you weighed the tradeoff. Reckless debt means nobody weighed anything.

The combo you want is *deliberate and prudent*. You made a call, you knew what you were doing, and you wrote it down somewhere a future engineer might find it.

### Who feels it

Engineers feel it first, because they're the ones reading the code every day. After that it spreads outward. New features take longer. Estimates get wider. The team starts saying "we should rewrite this" in standup. Eventually customers notice. Fewer releases, more bugs in the ones that ship.

The trick is that debt is mostly invisible to people who don't read code. Which is why every engineering leader I know has had some version of the conversation: *"It looks like we're not shipping much, but I promise we're spending all our time on something."*

### Keeping it from getting out of hand

A few things I've found genuinely help:

**Keep dependencies fresh.**  Old framework versions and abandoned libraries are a slow leak. Update them while it's still cheap. The longer you wait, the bigger the jump.

**Write down the known-bad parts.**  Doesn't need to be fancy. A `TODO.md` or a Confluence page listing the dragons you know about. The worst debt is the kind nobody remembers exists until they step on it.

**Review code seriously.**  Not rubber-stamp reviews. Real ones, where someone reads the change and asks why. Most debt I've seen in the wild would have been caught by a careful reviewer if anyone had been doing careful reviews.

**Have tests.**  Refactoring without tests is hoping. Tests give you the courage to clean things up instead of working around them.

**Modular boundaries you can defend.**  Architecture that lets you swap pieces in and out without rewriting the world. You don't get this for free. You have to fight for it.

**Blameless post-mortems.**  When something breaks, the question is "what made this possible," not "who did it." If your culture punishes mistakes, your team will hide the debt instead of fixing it.

### Once you've got debt, what then?

You'll always have some. The question is what you do about it.

- **Pay down the loud stuff first.** The files everyone is afraid to touch. The module that breaks every other sprint. That's where the interest is highest.
- **Boy Scout rule.** Leave the file a little better than you found it. Five to fifteen percent of every sprint, in my experience, is roughly what it takes to keep up.
- **Bundle cleanup with features.** Telling the business "we need a whole sprint for cleanup" is a losing argument. Telling them "this feature needs X, and while we're in there we'll fix Y" tends to win.
- **Sometimes you let it sit.** A prototype that's getting thrown away in three months doesn't need a refactor. Be honest about which code matters.

### The point

Debt isn't the enemy. *Ignored* debt is. The teams that ship best aren't the ones with the cleanest codebases. They're the ones who know exactly where the messes are and have a plan for the ones that matter.
