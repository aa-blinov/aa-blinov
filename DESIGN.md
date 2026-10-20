---
name: aa-blinov
description: The GitHub profile page of Alexander Blinov, rendered from a single Markdown file.
colors:
  primary: "#24292f"
  neutral-bg: "#ffffff"
typography:
  body:
    fontFamily: "system-ui, -apple-system, Segoe UI, sans-serif"
    fontSize: "16px"
    fontWeight: 400
    lineHeight: 1.6
  title:
    fontFamily: "system-ui, -apple-system, Segoe UI, sans-serif"
    fontSize: "32px"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "-0.02em"
rounded:
  md: "6px"
spacing:
  sm: "8px"
  md: "16px"
---

# Design system: aa-blinov

## Overview

**Creative North Star: "a business card, printed well"**

This repository owns no visual identity. The product is one Markdown file,
`README.md`, and GitHub renders it on the owner's profile page. There is no
stylesheet, no script, no component, no asset and no font file in the tree.
Every pixel a visitor sees belongs to GitHub's renderer.

What the repository does own is the writing: the order of the sections, the
level of each heading, the set of badges, the wording of the links. That is
the whole design surface, and the frontmatter above records GitHub's values
rather than this project's own, because there are none of its own to record.
The prose below says what the page does with them.

The decisions the page makes are all editorial. It opens with the roles
rather than with a greeting, keeps the areas of work to one short list, and
puts the contact route at the end of the first screen. It uses GitHub's own
Markdown and nothing else.

Confirmed rejections: no custom CSS, no HTML layout, no images, no SVG logo,
no icon set, no web font, no analytics script. GitHub sanitises most of that
on a profile page anyway, and a link that renders on GitHub and nowhere else
is a broken link for anyone who clones the repository.

Key characteristics:

- one screen of summary, then the links;
- plain Markdown that renders the same on GitHub and in a local checkout;
- English, for a reader who is not in the field;
- no emoji, no claim that the repository cannot verify.

## Colors

The page defines no colour. The values in the frontmatter are GitHub's light
theme, and they are recorded so that the rest of the document has something
to point at.

### Primary

- **Text** (`#24292f`): the default body colour on the light theme. GitHub's
  dark theme substitutes its own value, and the page does not try to hold
  either one.

### Neutral

- **Surface** (`#ffffff`): the page background on the light theme.
- **Muted** (`#57606a`): the colour GitHub uses for secondary text such as
  the badge alt text and the link underline.

### Named rules

**The Borrowed Surface Rule.** Every colour on the page comes from GitHub.
The page adds none, and no rule in this repository may name a hex value.

## Typography

**Display Font:** the system stack, `system-ui, -apple-system, Segoe UI,
sans-serif`.
**Body Font:** the same stack. There is no second family.

GitHub picks the stack and the sizes, and it picks them per viewport. The
page's job is to use the levels in a fixed order.

- **Title** (700, 32px, 1.2, -0.02em): the level-1 heading at the top of the
  file. It carries the name of the page, and nothing else is above it.
- **Section** (700, 24px): the level-2 headings. The page uses them for
  `Quick start`, `What it does`, `Connect`, `Interests`, `Development` and
  `License`, in that order.
- **Body** (400, 16px, 1.6): the paragraphs, and the list items that carry
  the areas of work.
- **Label** (400, 14px): the small print under the badges, and the list
  items under `Connect`.
- **Code** (400, 13px, monospace): the fenced command blocks and the inline
  code spans. GitHub renders both in its own monospace stack.

### Named rules

**One Level Per Meaning.** A level-2 heading names a part of the page, and
nothing else uses one. There is no level-3 heading in the file, because the
page has no part that needs a subsection.

## Layout

A single column. GitHub caps the reading width and centres it, and the page
does not set a width, a margin or an alignment.

The vertical order is fixed, and it follows the order of the reader's
questions: the name, the badges, a rule, then how to run it, then what the
owner works on, then how to reach the owner, then the interests, then the
quotation, then the development notes, then the licence.

The spacing between blocks comes from GitHub's scale, 8px inside a list and
16px between blocks. The page adds no spacing of its own, and it has no
grid, no sidebar, no table of contents and no anchors.

On a phone the column narrows to the viewport and the lists wrap. Nothing on
the page is positioned, so nothing can overlap when it does.

## Elevation & Depth

There is none, and there is nothing to say about it. GitHub's renderer draws
a profile README flat: no shadows, no raised cards, no overlapping layers.
The badges are the only bordered objects on the page, and they are flat
pictures with a 6px radius.

## Shapes

The page draws no shapes. The rounded corners a visitor sees belong to the
badges, to the avatar and to the code blocks, and GitHub sets all three.

## Components

The components of this page are Markdown blocks. Each one has a fixed job,
and there is no other way to build the page.

### Headings

- **Shape:** none. The glyphs are GitHub's.
- **Usage:** one level-1 heading, then level-2 headings. No level 3.
- **Rule:** the level-2 headings stay in the order listed under Layout, so
  the page reads the same on every visit.

### Badges

- **Shape:** a remote image from `img.shields.io`, 6px radius, 20px tall.
- **Usage:** two of them, the licence and the house-style workflow, both
  under the first paragraph and both pointing at the file or the workflow
  they name.
- **Rule:** a badge links to what it claims. A badge whose target is
  missing is worse than no badge.

### Lists

- **Shape:** GitHub's markers, 8px apart.
- **Usage:** two of them. The areas of work, with the label in bold, and the
  contact links, without one.
- **Rule:** the bold label carries the name of the thing, and the rest of
  the item says what it is.

### Blockquote

- **Shape:** a vertical rule on the left, GitHub's.
- **Usage:** once, at the end, for the sentence about collaboration.

### Code

- **Shape:** a grey block with a 6px radius.
- **Usage:** twice, for the clone command and for the house-style check.
- **Rule:** every command in the file is one that runs.

### Horizontal rule

- **Shape:** a 1px line the width of the column.
- **Usage:** once, between the badges and the first section.

## Do's and Don'ts

### Do:

- **Do** keep the summary to one screen before the contact links.
- **Do** name the roles, the employers and the tools as the owner writes
  them.
- **Do** keep the two badges, and point each at the file or the workflow it
  names.
- **Do** check that every link resolves before the pull request merges.
- **Do** state the licence and link `LICENSE`.

### Don't:

- **Don't** add HTML, CSS, scripts or images. The profile renderer drops
  them, and the page looks broken to the reader who finds it.
- **Don't** add emoji. HS040 fails the build on the glyph, and the first
  version of this page carried one from GitHub's own template.
- **Don't** add skill bars, percentages or years of experience. Nothing on
  the page can be checked, and the owner did not write them.
- **Don't** add counters, badges for downloads or a hit counter. There is
  nowhere to count, and a number nobody can trace is noise.
- **Don't** put a second level-1 heading in the file. GitHub renders one,
  and the checker's HS011 fails on the second.
