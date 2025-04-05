---
title: 'Why I Switched from WordPress to Astro'
description: "I'd been running this site on WordPress for over a decade. Here's why I finally moved it to Astro."
pubDate: '2025-04-05'
heroImage: '/images/wordpress-to-astro.jpg'
---

I built my first websites on WordPress. This blog ran on WordPress for somewhere north of a decade. I'm still fond of it. But a few months ago I rebuilt the whole thing on [Astro](https://astro.build/), and I haven't looked back.

This is the story of why.

### The thing that finally pushed me

WordPress wasn't broken. That's not why I moved. It was the *maintenance tax*.

Every few weeks I'd log in to find: PHP version update warnings, plugin updates, theme updates, a security patch, a plugin that hadn't been updated by its author in two years and was now flagging as a risk. None of it was hard individually. All of it added up.

I write about a dozen posts a year. The ratio of "time spent maintaining the site" to "time spent writing on the site" had crept up to something embarrassing. So I started looking around.

### Why Astro, specifically

I looked at the usual suspects: Next.js, Eleventy, Hugo, Gatsby (RIP). Astro won on a few axes that mattered to me:

- **It generates static HTML by default.** No runtime, no PHP, no database queries on every page load. The output is files. Files are easy.
- **Zero JavaScript unless I ask for it.** Most pages on a personal blog don't need any. Astro ships none by default and lets me opt in to React or Svelte islands where I need interactivity.
- **Markdown content with proper frontmatter.** My old posts came out of WordPress as messy HTML soup. Astro happily eats Markdown, which means going forward I'm writing in plain text files in a git repo, not a CMS.
- **It got out of my way.** No opinionated routing, no required state library, no framework lock-in.

I deploy the built site to Cloudflare Pages. End to end, a `git push` to a live update takes about 30 seconds.

### What I gave up

Honest list, because it's not all upside:

- **The WordPress editor.** Love it or hate it, Gutenberg is genuinely good for non-technical writers. If my wife wanted to publish a post tomorrow, she could on WordPress. On Astro she'd need to write Markdown, commit, and push. That's a tradeoff that works for me but wouldn't work for everyone.
- **Plugins for everything.** Want a contact form? You're writing it. Want comments? Pick a third-party service. Want analytics? Drop in a script. WordPress had a one-click solution for all of these.
- **The dashboard.** I miss the dashboard, a little. Mostly I don't.

### Was it worth it

For me, yes. The site is faster, costs less, and I haven't applied a security update in months because there's nothing to patch. Writing posts feels lighter. I open VS Code instead of a browser tab.

WordPress is still the right answer for plenty of sites. If you're running a small business that needs e-commerce, contact forms, a booking system, and a blog, and you want one person to manage the whole thing from a browser, WordPress is still excellent at that.

But for a personal blog written by an engineer who already lives in a terminal? Astro fits like a glove.
