---
title: "5 Ways to Organize Jira Projects"
description: ""
pubDate: "2022-12-05"
heroImage: "/images/jira.jpg"
category: "Jira"
tags: ["Jira", "Jira Projects", "Jira Workflow"]
---

## Pick the structure that matches how your org actually works

Most engineering orgs I've worked with default to one Jira project per team and then never revisit the decision. Sometimes that's the right call. Often it isn't.

A Jira project is a bucket of issues that share configuration, permissions, versions, and workflow. So when you're picking how to organize projects, you're really picking the answer to four questions. Who moves issues through the workflow? Who needs to see what? Which issues belong together for reporting and versioning? And how much friction do you want when the org reshuffles next year?

There's no single right answer. Here are five patterns I've seen work, with the tradeoffs that come with each.

### 1. By team

The default. One project per team. Easy to set up, easy to reason about, and great when teams are self-contained and don't hand work back and forth.

It falls apart the moment your org chart starts changing. Every reorg means reshuffling project settings, permissions, members, and sometimes workflows. If your team boundaries shift often, this model becomes a tax.

### 2. By business unit

Instead of one project per team, one project per function. Engineering, Product, Customer Success, and so on. Good when team boundaries are fluid but functional boundaries are stable, and when the work inside a function follows similar patterns.

The catch is that most real work crosses functions. If your Customer Success folks are constantly filing issues that engineering owns, you'll start fighting the structure.

### 3. By product line

One project per product. This works well when a product is built by multiple teams across multiple functions and ships on a shared release cycle. Versioning lines up cleanly with the product. Cross-functional work happens inside the project rather than between projects.

Probably my favorite default when the org is built around products.

### 4. By platform

Same idea as product line, but the unit is a platform. iOS, Android, the ad platform, whatever you ship onto. Useful when teams are organized around platform delivery rather than product, and when releases are tied to a platform's cadence.

### 5. By business objective

One project per OKR, initiative, or company-wide bet. Useful when work is both cross-functional and cross-product, and you need to see all activity tied to a specific outcome together.

I'd rather use Initiatives or Themes for this and let projects stay structured around teams or products. That way one objective can roll up work from multiple projects, which is closer to reality.

A bit of thought up front saves you from a Jira instance that nobody trusts and everyone fights. Pick the model that matches how your org actually delivers work, not the one that matches your org chart.
