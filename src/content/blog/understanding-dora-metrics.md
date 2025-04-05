---
title: 'Understanding DORA Metrics'
description: 'What DORA metrics tell you, what they leave out, and how to use them without turning your team into a dashboard.'
pubDate: '2023-03-13'
heroImage: '/images/dora.jpg'
---

DORA metrics are everywhere now. Every engineering leadership deck, every observability tool's marketing site. Which is great, because there are real ideas in there. It's also a problem, because once a number ends up on a dashboard, somebody starts optimizing for the number instead of the thing the number was a proxy for.

Here's how I think about them.

### Where they came from

DORA stands for DevOps Research and Assessment, the group behind *Accelerate*, eventually acquired by Google. The headline finding from years of their research: four specific signals do a decent job of separating high-performing engineering orgs from the rest.

The four:

1. **Cycle time** (commit to production)
2. **Deployment frequency**
3. **Change failure rate**
4. **Mean time to recover**

Two speed metrics, two stability metrics. The pairing is the point.

### Why the pairing matters

If you only watch deployment frequency, you'll get teams that ship constantly and break everything. If you only watch change failure rate, you'll get teams that don't ship at all because shipping is risky. The metrics check each other.

That's the part that gets lost when these things become a scoreboard. They're not goals. They're vitals. Like a fever: it tells you something is happening, not what to do about it.

### Cycle time

How long does code take to get from a commit to running in production?

It's the most useful of the four for me, because it cuts across so many things. A slow cycle time can mean:

- Review takes forever
- CI is flaky
- Merges block on tickets, approvals, calendar slots
- The release process involves a human running a script at 4pm on a Tuesday

Each of those is a different fix. The number itself doesn't tell you which. You have to look.

Common sub-cuts: WIP (first commit to last commit), review time, merge time, release time. Any of those getting noticeably worse is worth a conversation.

### Deployment frequency

How often you push to production. Small frequent deploys are easier to debug, easier to roll back, and easier to reason about than big batched ones. That's well established.

The trap is treating "more deploys" as the goal. You can game this by counting every config push, or by deploying nothing of consequence ten times a day. The number is meaningless without the change failure rate next to it.

### Change failure rate

What percentage of deploys cause an incident, rollback, or hotfix?

This one is the most honest of the four, because nobody enjoys reporting a high number. Definitions vary. Some teams count anything that needed a follow-up, others only count user-visible incidents. Pick one, write it down, and don't change it every quarter.

A creeping change failure rate usually means one of: tests aren't catching the things they should, the team is under deadline pressure and skipping review, or the deploy pipeline lacks safety nets like canaries and progressive rollouts.

### Mean time to recover

When something breaks, how long until it's fixed? This is the resilience number.

Two sub-cuts I find useful:

- **MTTA**, time to acknowledge. How long before someone *knows*.
- **MTTRepair**, time to fix it.

If MTTA is bad, your alerting is bad. If MTTRepair is bad, your runbooks, observability, or on-call rotation are bad. They're different problems.

### Using them well

A few things I've learned the hard way:

Don't make them OKRs. The minute they show up on someone's performance review, they stop being honest signals and start being targets to hit.

Watch trends, not absolute numbers. "Our cycle time is 3.2 days" means little. "Our cycle time has doubled over the last quarter" means quite a lot.

Talk about them in retros, not in dashboards-only-leaders-see. The team should know what the numbers are doing and why.

And don't treat them as the full picture. They tell you nothing about morale, about whether the right things are being built, or about whether the architecture is going to fall over in eighteen months. They're vitals. You still need a doctor.
