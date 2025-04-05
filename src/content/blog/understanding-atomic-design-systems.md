---
title: 'Understanding Atomic Design Systems'
description: 'A practical look at Atomic Design, the methodology I keep coming back to when I need to structure a UI library.'
pubDate: '2017-07-21'
heroImage: '/images/atomic-design.jpg'
category: 'Design'
tags: ['Design Systems', 'Atomic Design', 'UX']
---

I've worked on a lot of UI libraries. The ones that held up were the ones with a real structure underneath. The ones that fell apart were the ones where every screen invented its own buttons.

Atomic Design is the structure I reach for. It's not the only way to organize a design system, but it maps cleanly to how I already think about composition in code, so it sticks.

## A Design System, Briefly

A design system is the shared vocabulary your team uses to build product. Tokens, components, patterns, the docs around them. [Bootstrap](https://getbootstrap.com/) is the example everyone knows. You get buttons, forms, and a grid, and any developer can read the markup and know what they're looking at.

The same instincts that make for good software (modularity, reuse, don't repeat yourself) make for good design systems. That overlap is why this stuff resonates with engineers in the first place.

## Atomic Design

[Brad Frost](https://bradfrost.com/blog/post/atomic-web-design/) wrote the book on this. The idea is to take chemistry as a mental model and structure your UI in five layers: Atoms, Molecules, Organisms, Templates, and Pages. Small things compose into bigger things. You build up, not out.

### Atoms

Atoms are the smallest pieces. A button. An input. A label. A heading style. Break them down further and they stop being useful.

Atoms have variants (`btn-primary`, `btn-danger`) but each variant should have a job. If two variants do the same thing, you have one variant with a bad name.

### Molecules

Molecules are small groups of atoms doing one job together. Google's search box is the canonical example: a text input, a search button, and a microphone icon, glued together into a search-the-web component.

The job is what makes it a molecule. If you can't describe what it does in one sentence, it's probably too big.

### Organisms

Organisms are sections of UI built from molecules and atoms. A site header. A product card grid. A blog post carousel with its nav controls and article previews.

This is the layer where the page starts to feel like a page. Organisms are usually where I draw the line between "library component" and "feature code," though that line moves depending on the team.

### Templates

Templates are layouts. They wire organisms together into a page structure without committing to real content yet. Lorem ipsum, gray rectangles where the images go, that kind of thing.

The point is to argue about layout and flow before you argue about copy. I've watched teams spend two weeks on body text for a page that turned out to have the wrong structure. Templates head that off.

### Pages

Pages are templates filled with real content. Real names, real product photos, real edge cases. This is where layout assumptions either hold up or fall apart, which is why this step matters even though it feels redundant.

You don't need a page for every template. Use them when the content will tell you something the wireframe couldn't.

## Why It Works Outside the Browser

The reason Atomic Design holds up is that it's not really about HTML and CSS. It's about composition. Packaging design has the same shape: barcodes and nutrition labels are atoms, an ingredient panel is a molecule, the back of a cereal box is a template. Same with furniture. Same with book design.

Anywhere you build complex things out of small repeatable parts, this model fits.

## What I'd Tell You to Do

Start with the atoms you actually use. Not the atoms you think you'll need. Go look at your product, list the buttons and inputs and labels that show up across screens, and start there. Compose up from those.

A design system that grows out of real product is the one your team will actually use. A design system you write in a vacuum is the one that ends up in a Figma file no one opens.
