---
title: "Your SaaS Isn't Production-Ready Until You Fix These 16 Things"
date: 2026-09-02
categories: [Web Development, DevOps]
tags: [SaaS, Frontend, SEO, Web Performance, React, Vite, Production, DevOps]
toc: true
comments: true
---

# Your SaaS Isn't Production-Ready Until You Fix These 16 Things

> *A working application isn't necessarily a production-ready application. Before shipping my SaaS, I went beyond the UI and code to make the product understandable, discoverable, performant, and actually ready for the web.*

---

# Introduction

There is a moment in almost every software project where you think:

> **"It's working. We can ship it."**

The authentication works.

The API works.

The database works.

The UI looks good.

The production build passes.

So you're done.

Right?

Not quite.

Recently, while preparing one of my SaaS applications for production, I decided to stop looking at it purely as a developer.

Instead, I looked at it as:

- a user
- a browser
- a search engine
- a crawler
- an accessibility tool
- a performance auditor
- and increasingly, an AI system

That changed the way I looked at the application.

The product worked, but there were still plenty of things that made it feel like a **developer-built application rather than a finished product**.

So I went through a production-hardening pass.

The checklist ended up looking like this:

1. Build a proper page source
2. Build a custom 404 page
3. Give every page a unique title
4. Write useful meta descriptions
5. Add canonical tags
6. Use a unique heading structure
7. Generate `sitemap.xml`
8. Configure `robots.txt`
9. Add `llms.txt`
10. Replace the default favicon
11. Add internal links and breadcrumbs
12. Add structured data
13. Fix every production console error
14. Define a production source-map strategy
15. Reduce huge JavaScript bundles
16. Remove every Vite + React placeholder

None of these tasks is particularly glamorous.

But together, they make a huge difference.

---

# 1. Build a Proper Page Source

One of the first things I did was stop judging the website only by what I could see in the browser.

I opened the actual page source.

Modern frontend frameworks make it incredibly easy to build an application where the browser eventually renders everything correctly, while the initial HTML contains very little meaningful information.

That can become a problem for:

- search engines
- crawlers
- link previews
- accessibility tools
- other automated systems

A page should expose meaningful information about itself.

That means having things like:

```html
<title>...</title>
<meta name="description" content="...">
<link rel="canonical" href="...">
```

along with semantic HTML and useful content.

The browser shouldn't have to guess what the page is about.

---

# 2. Build a Custom 404 Page

A missing page shouldn't lead to a blank screen or a generic server error.

I built a proper 404 page that:

- matches the application's branding
- clearly tells the user what happened
- provides navigation back into the application
- links to useful sections
- maintains the same visual language as the rest of the product

A 404 page is still part of your product.

Someone reached it because something went wrong.

That's exactly when the application should help them recover.

---

# 3. Give Every Page a Unique Title

A surprisingly common problem in single-page applications is having the same page title everywhere.

Something like:

```text
My SaaS
```

doesn't tell you much.

Compare that with:

```text
Dashboard | My SaaS
Pricing | My SaaS
Documentation | My SaaS
AI Video Editor | My SaaS
```

Each page now has an identity.

Unique titles improve:

- browser usability
- bookmarks
- search result understanding
- link previews
- accessibility

The title should describe the actual page, not simply repeat the company name.

---

# 4. Write Meta Descriptions That Actually Describe the Page

I also went through the meta descriptions.

The goal wasn't to stuff keywords into them.

The goal was to answer one simple question:

> **"What will I find if I open this page?"**

A page about pricing should describe pricing.

A page about a product feature should describe that feature.

A documentation page should describe what the documentation contains.

Generic descriptions like:

> "The world's best platform for creators."

don't provide much useful context.

Good metadata should be useful to humans as well as machines.

---

# 5. Add Canonical Tags

Another thing I checked was canonicalization.

The same content can sometimes become accessible through multiple URLs because of:

- query parameters
- trailing slashes
- campaign URLs
- routing behavior
- alternate paths

For important public pages, I added canonical URLs so there is a clear preferred version.

For example:

```html
<link
  rel="canonical"
  href="https://example.com/pricing"
/>
```

The important part is consistency.

The canonical URL should match the URL strategy used across the site.

---

# 6. Give Every Page a Clear Heading

A page can look perfect visually while having a terrible document structure.

I started checking the actual heading hierarchy.

The primary purpose of the page should be represented by a meaningful `H1`.

Then supporting sections should use appropriate `H2` and `H3` elements.

For example:

```text
H1 → Pricing

H2 → Plans
H2 → Features
H2 → Frequently Asked Questions

H3 → Free Plan
H3 → Pro Plan
H3 → Enterprise
```

This isn't about blindly following an SEO rule.

It's about making the document structure make sense.

---

# 7. Generate `sitemap.xml`

If a site contains public pages that should be discoverable, those pages should have a clear sitemap strategy.

I added a `sitemap.xml` containing the important public URLs.

But there is an important distinction:

**A sitemap isn't a dumping ground for every URL your application can generate.**

It should contain URLs that are:

- public
- canonical
- useful
- intended for discovery

Authenticated dashboards and internal application routes don't belong there just because they exist.

---

# 8. Configure `robots.txt`

Next came `robots.txt`.

This provides crawler-level guidance about which parts of the application should or shouldn't be crawled.

For a SaaS application, you might have:

```text
/
├── marketing/
├── blog/
├── docs/
├── pricing/
├── dashboard/
├── settings/
└── admin/
```

The public sections and authenticated application sections have completely different purposes.

The important thing is to deliberately decide what should be discoverable instead of leaving the crawler configuration as an afterthought.

---

# 9. Add `llms.txt`

This is one of the newer additions to my checklist.

Traditional web optimization has mostly focused on search engines.

But websites are increasingly being consumed by AI systems too.

I added an `llms.txt` file containing concise information about the product and important resources.

The bigger idea is interesting:

> **The web isn't only being indexed by search engines anymore.**

AI systems are increasingly becoming another layer through which users discover and interact with information.

Whether `llms.txt` becomes a universal standard or not, thinking about machine-readable product context is valuable.

---

# 10. Replace the Default Favicon

This sounds ridiculously small.

It isn't.

A favicon appears in:

- browser tabs
- bookmarks
- browser history
- shortcuts
- search interfaces
- other browser surfaces

Leaving the default framework favicon behind immediately makes a product feel unfinished.

So I replaced the development placeholder with a favicon that actually belongs to the product.

The rule is simple:

> **If the user can see it, brand it properly.**

---

# 11. Add Internal Links and Breadcrumbs

I also looked at how pages connected to each other.

A website shouldn't be a collection of isolated pages.

Important relationships should be visible.

For example:

```text
Home
  ↓
Products
  ↓
AI Video Editor
  ↓
Documentation
```

Internal links help users discover related content.

They also give crawlers additional context about the relationship between pages.

Where the site's information architecture justified it, I also added breadcrumbs.

For example:

```text
Home → Documentation → API → Authentication
```

Now the hierarchy is obvious.

---

# 12. Add Structured Data

Humans understand websites visually.

Machines don't have that same advantage.

Structured data provides additional machine-readable context about what a page represents.

Depending on the page, this can include:

- organization information
- software/application information
- articles
- breadcrumbs
- FAQs
- other supported structured entities

For example, breadcrumb navigation can have corresponding breadcrumb structured data.

The important rule is:

> **Structured data should describe what is actually present on the page.**

Don't generate schema just because you can.

---

# 13. Fix Every Production Console Error

This became one of my favorite rules:

> **A production console should be boring.**

No unexplained errors.

No failed requests.

No hydration problems.

No broken assets.

No mysterious warnings that everyone has become accustomed to ignoring.

I went through the browser console and fixed the actual problems instead of simply hiding them.

Console noise is dangerous because it creates alert fatigue.

When everything is red, eventually nobody notices the thing that actually matters.

---

# 14. Define a Production Source-Map Strategy

Source maps are extremely useful during development.

They make debugging bundled JavaScript dramatically easier.

But production source maps deserve a deliberate strategy.

Depending on the application, publicly serving source maps may expose more implementation detail than intended.

So instead of blindly shipping them, I decided what the production environment actually needed.

For example:

```text
Development
    ↓
Full source maps

Production
    ↓
Private source maps
    ↓
Error monitoring / debugging platform
```

The point isn't:

> "Source maps are bad."

The point is:

> **Don't accidentally expose development artifacts just because the build tool generated them.**

---

# 15. Reduce Huge JavaScript Bundles

Then I looked at the production JavaScript.

This is where things got interesting.

A landing page shouldn't need to download the entire application before it can become useful.

I started looking for:

- oversized dependencies
- unused packages
- globally imported libraries
- components loaded too early
- routes that could be code-split
- duplicate dependencies
- unnecessary client-side JavaScript

For example, instead of loading everything immediately:

```text
Application
    ↓
Everything
    ↓
Browser downloads everything
```

I wanted:

```text
Application
    ↓
Critical code
    ↓
Initial render

User opens feature
    ↓
Load feature code
```

Code splitting and lazy loading can make a huge difference here.

Performance isn't just a Lighthouse number.

It's about how much work the user's device actually has to do.

---

# 16. Remove Every Vite + React Placeholder

Finally, I searched the application for traces of the original scaffolding.

And there were more than I expected.

Things like:

- Vite references
- React references
- default favicons
- placeholder metadata
- starter assets
- demo copy
- development URLs
- example components
- default README content
- unused starter files

A production application shouldn't advertise the framework that was used to bootstrap it unless that information is actually relevant.

So I did a repository-wide cleanup.

Search.

Delete.

Replace.

Build.

Search again.

---

# The Before/After

This wasn't a complete rewrite of the application.

The product already worked.

The difference was everything around the product.

## Before

The application was functional, but it still had several signs that it had been built primarily from a developer's perspective.

- Generic or duplicated page titles
- Weak metadata
- Missing canonical URLs
- Default framework favicon
- Incomplete 404 experience
- Weak internal linking
- Missing breadcrumb structure
- Missing structured data
- Production console noise
- Unnecessary development artifacts
- Large JavaScript bundles
- Vite/React traces
- No deliberate crawler configuration
- No machine-readable product context

Nothing was necessarily catastrophic.

That's what made it easy to ignore.

## After

The application started behaving more like a real product.

Every important page had a clear identity.

The page source actually described what the page was.

The canonical URL strategy was explicit.

The 404 page belonged to the product.

Internal links reflected the application's information architecture.

Breadcrumbs communicated hierarchy.

Structured data provided additional machine-readable context.

The production console became quiet.

The frontend stopped shipping unnecessary code.

Development artifacts were removed.

And the application no longer looked like a Vite + React starter that happened to become a SaaS.

The biggest change wasn't visual.

It was **clarity**.

---

# What I Actually Learned

The biggest lesson wasn't really about SEO.

It was about **finishing**.

As developers, we naturally focus on the difficult parts.

We think about:

- databases
- APIs
- authentication
- payments
- AI pipelines
- background workers
- cloud infrastructure
- CI/CD

Then the feature works.

And our brain says:

> "Done."

But production readiness is another layer.

The browser needs to understand the application.

Search engines need to understand the pages.

Users need to understand where they are.

Accessibility tools need meaningful structure.

Crawlers need clear signals.

And increasingly, AI systems are becoming another way users discover information.

I also learned that performance optimization shouldn't start with blindly chasing a score.

Start with the actual application.

Find what is being downloaded.

Find what is being executed.

Find what isn't necessary.

Then remove it.

The same principle applies to metadata.

Don't add a title because an SEO checklist told you to.

Ask:

> **"What is this page actually about?"**

Then make the HTML say exactly that.

Good production engineering is often less about adding things and more about removing things that shouldn't be there.

---

# My Production Checklist

This is the checklist I'm keeping for future SaaS projects.

## SEO & Discoverability

- [ ] Meaningful page source
- [ ] Unique `<title>` for every important page
- [ ] Unique meta description
- [ ] Canonical URL
- [ ] Clear primary heading
- [ ] Internal links
- [ ] Breadcrumb navigation where appropriate
- [ ] `sitemap.xml`
- [ ] `robots.txt`
- [ ] `llms.txt`

## Structured Data

- [ ] Organization/application schema where appropriate
- [ ] Article schema for articles
- [ ] Breadcrumb schema
- [ ] Validate structured data
- [ ] Ensure schema matches visible content

## UX & Branding

- [ ] Custom 404 page
- [ ] Product-specific favicon
- [ ] No placeholder copy
- [ ] No default framework assets
- [ ] No broken links
- [ ] Clear navigation paths

## Frontend Quality

- [ ] Zero unexplained console errors
- [ ] Zero unnecessary warnings
- [ ] No failed network requests
- [ ] No hydration/runtime errors
- [ ] Production source-map strategy defined
- [ ] No publicly exposed development artifacts

## Performance

- [ ] Analyze production bundle
- [ ] Remove unused dependencies
- [ ] Code-split large routes
- [ ] Lazy-load non-critical components
- [ ] Reduce initial JavaScript
- [ ] Optimize images and fonts
- [ ] Avoid globally loading page-specific libraries

## Final Cleanup

- [ ] Search for `Vite`
- [ ] Search for `React`
- [ ] Search for placeholder text
- [ ] Search for demo/test content
- [ ] Search for development URLs
- [ ] Search for unused assets
- [ ] Verify production environment variables
- [ ] Test important routes directly
- [ ] Test 404 behavior
- [ ] Inspect page source
- [ ] Test in a clean browser session
- [ ] Run the production build again

---

# Final Thoughts

There is a weird stage in every project where the application technically works but still doesn't feel finished.

I think that's where most of this work belongs.

Not after users discover the problems.

Not after a search engine fails to understand your pages.

Not after someone opens DevTools and finds a wall of errors.

Before shipping.

I want to be able to open the application and think:

> **There is nothing here that tells the user this is an unfinished developer project.**

The source is clean.

The metadata makes sense.

The navigation makes sense.

The errors are gone.

The bundles are reasonable.

The branding is consistent.

The crawlers have clear signals.

The machine-readable context exists.

And the application doesn't accidentally advertise the framework that created it.

That's the point where I consider the frontend **shipped**, rather than merely **built**.

The feature got me here.

The boring details made it production-ready.

---

# Final Checklist

```text
✓ Proper page source
✓ Custom 404
✓ Unique page titles
✓ Useful meta descriptions
✓ Canonical URLs
✓ Semantic headings
✓ sitemap.xml
✓ robots.txt
✓ llms.txt
✓ Product favicon
✓ Internal links
✓ Breadcrumbs
✓ Structured data
✓ Clean production console
✓ Production source-map strategy
✓ Optimized JavaScript bundles
✓ Zero Vite/React placeholders
```

**Build the feature.**

**Harden the product.**

**Then ship it.**
