---
title: 'Design Systems: More Than a Style Guide'
description: 'What a design system is, what it is not, and how to start one without losing six months to it.'
pubDate: '2019-11-13'
heroImage: '/images/design-system.jpg'
category: 'UI/UX'
tags: ['design systems', 'ui development', 'design consistency']
---

Every team I've worked on has eventually run into the same question: where do we keep the buttons. Not literally the buttons, but the shared rules about how the product looks and behaves. The answer is a design system, and the longer you put off building one, the more expensive the buttons get.

## What a Design System Is

A design system is the shared source of truth for how your product is designed and built. Tokens, components, patterns, documentation, the code that backs all of it. It lives at the intersection of design and engineering, and when it works, both groups stop arguing about what a "primary button" means.

It's not a style guide. A style guide is a PDF. A design system is code your team ships against.

## Why It's Worth It

A few things change when you have one.

**Consistency stops being a manual task.** You're not asking a designer to verify the padding on every screen. The component does it. When the component changes, everything that uses it changes.

**QA gets cheaper.** When the same primitives back every screen, defects start to look obvious. A button that looks weird stands out because every other button looks right.

**Design and engineering speak the same language.** "Secondary button" means one thing. Not "the blue one with the outline that James used on the settings page." Naming things well prevents a surprising amount of rework.

**Building features feels like assembly.** New screen, three existing organisms, some product-specific glue, done. You're not relitigating type scale every sprint.

**Designers get to do design.** When the foundational decisions are made and durable, the work shifts to user flows, accessibility, and the parts of the experience that actually need attention.

## Systems Worth Reading

A few I've learned from:

- [Material Design](https://material.io/design), Google's
- [Atlassian Design System](https://atlassian.design/components), well-documented and pragmatic
- [Polaris](https://polaris.shopify.com), Shopify's
- [Carbon](https://carbon.design), IBM's
- [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines), Apple's
- [Nachos](https://nachos.io), Trello's, with the best illustrations
- [Grommet](https://grommet.io), HP's open one

Read them. Steal liberally. Most of the hard questions have been answered somewhere on this list.

## Do You Need One

Yes. Even small teams. The argument that you're too early is the same argument that ends with twelve flavors of card component in production.

Start light. A token file, half a dozen components, a README. That's a design system. Let it grow from there.

## Getting Started

You're in one of two situations.

### Greenfield

If you're starting fresh, the design work comes first. Once a visual direction is settled, move into the system:

- Tokens first: color, type, spacing, radii.
- Then primitives: button, input, icon, link.
- Then patterns: nav, forms, cards.
- Then page templates that compose those patterns.

The atomic model (tokens, atoms, molecules, organisms, templates) is a decent scaffold. Don't be religious about the layers.

### Retrofit

Existing product. Open up your app, take screenshots of every button, every input, every card. You'll be horrified. Group them by intent, kill the duplicates, name the survivors. Then refactor toward that smaller set, one screen at a time.

Retrofits are slower than greenfield work, but they pay off faster because every consolidated component pulls real screens with it.

## One More Thing

The design system that gets used is the one your team helped build. Pull a designer and an engineer into it from week one. The thing you hand down from on high will sit on a shelf next to the style guide PDF.

Start small. Ship it. Let it grow with the product.
