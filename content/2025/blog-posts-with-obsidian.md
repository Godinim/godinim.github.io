---
title: Quartz Blog Posts with Obsidian
aliases:
  - "Project Showcase: Static Blog Posts with Obsidian"
  - Static Blog Posts with Obsidian Review Draft
  - Quartz Blog Setup
tags:
  - AI
  - Obsidian
  - Quartz
  - GitHub-Pages
date: 2025-11-23
github: https://github.com/Godinim/godinim.github.io
tools:
  - Obsidian
  - Quartz
  - GitHub
  - GitHub Pages
  - GitHub Actions
  - Quartz Syncer
concepts:
  - Static site generation
  - Markdown publishing
  - Digital garden
  - Git-based deployment
  - Knowledge management
summary: Publishing Obsidian notes as a static website using Quartz, GitHub Pages, and a lightweight Git-based workflow.
publish: true
---

# Static Blog Posts with Obsidian

> **Tagline**: Turn a working Obsidian vault into a fast, low-maintenance website without rebuilding your writing workflow from scratch.

---

## Purpose

I wanted a simple way to publish notes and project writeups from [[Obsidian]] to the web. The end goal was not just a blog, but a lightweight portfolio and knowledge base that could live on static hosting with minimal moving parts.

After testing a few options, I landed on [[Quartz]]. I played around with [Hugo](https://github.com/gohugoio/hugo) and [Obsidian Digital Garden](https://github.com/oleeskild/obsidian-digital-garden), but Quartz ended up being the best fit because it was built around Obsidian-style authoring, handled wikilinks cleanly, and had a stronger plugin and integration story for the workflow I wanted.

> [!info] Project Goals
>
> - Publish selected Obsidian notes as a static site
> - Keep hosting simple and cheap with GitHub Pages
> - Use Git-based deployment so updates are repeatable and low-friction
> - Support portfolio-style project pages alongside normal blog posts

**Key Results / Achievements / Techniques / Concepts**

- Evaluated multiple publishing approaches before standardising on Quartz
- Kept the authoring workflow inside Obsidian instead of writing directly in a web CMS
- Used GitHub Actions and GitHub Pages for automated deployment
- Added Quartz Syncer to make publishing from Obsidian more practical day to day

---

## Why Quartz

Quartz sits in a useful middle ground between a traditional static site generator and an Obsidian-native publishing workflow.

- **Hugo** is powerful, but it felt more website-first than note-first for this use case.
- **Obsidian Digital Garden** was closer to the right direction, but Quartz gave me more flexibility around structure, theming, and Obsidian compatibility.
- **Quartz** supports Obsidian-flavoured Markdown, wikilinks, Mermaid diagrams, callouts, backlinking, graph-style navigation, and GitHub Pages hosting without forcing me to abandon the way I already take notes.

That made it the most practical option for turning an internal knowledge system into a public-facing site.

## Tools & Technologies

| Tool / Technology | Description                                                       | Link / Port                                  |
| ----------------- | ----------------------------------------------------------------- | -------------------------------------------- |
| Obsidian          | Primary writing environment and source of truth for notes         | Local Vault                                  |
| Quartz            | Static site generator designed to work well with Obsidian content | https://quartz.jzhao.xyz/                    |
| GitHub            | Repository hosting and version control                            | https://github.com/Godinim/godinim.github.io |
| GitHub Actions    | Automated build and deployment pipeline                           | GitHub Actions                               |
| GitHub Pages      | Static hosting for the published site                             | GitHub Pages                                 |
| Quartz Syncer     | Obsidian plugin for publishing selected notes into a Quartz repo  | https://github.com/saberzero1/quartz-syncer  |

---

## Architecture & Workflow

```mermaid
graph LR
    A[Write in Obsidian] --> B[Sync selected notes to Quartz content]
    B --> C[Push changes to GitHub repository]
    C --> D[GitHub Actions build Quartz site]
    D --> E[Deploy to GitHub Pages]
    E --> F[Public blog and portfolio site]
```

The architecture is intentionally simple:

- Obsidian is the authoring layer
- Quartz is the publishing layer
- GitHub is the transport and automation layer
- GitHub Pages is the hosting layer

This keeps the workflow transparent and easy to debug. Notes remain normal Markdown files, the site can be rebuilt locally, and deployment is tied to the repository rather than a separate publishing platform.

---

## Implementation Steps

### Step 1: Bootstrap Quartz

- **Tool/Action:** Create a new Quartz site
- **Input:** A local development environment with Node.js and `npx`
- **Output:** A Quartz project scaffold ready to be configured

The starting point was creating the Quartz site locally:

```bash
npx quartz create
```

To preview the site during setup:

```bash
npx quartz build --serve
```

This local preview loop is useful because it keeps the content and theme iteration fast before anything is pushed upstream.

### Step 2: Connect the Repo to GitHub

- **Tool/Action:** Push the Quartz project into GitHub
- **Input:** Local Quartz repository
- **Output:** Remote repository ready for version control and deployment

Once the scaffold was working locally, the next step was pushing it into GitHub. That created a clean deployment path and made it easier to use GitHub Actions plus GitHub Pages as the hosting stack.

### Step 3: Publish Content from Obsidian

- **Tool/Action:** Use Quartz Syncer inside Obsidian
- **Input:** Selected notes from the vault
- **Output:** Notes copied into the Quartz `content` folder and committed to the publishing repo

Rather than manually copying Markdown files around, Quartz Syncer makes publishing much smoother. It lets me manage which notes should be published and push them into the Quartz repository from inside Obsidian.

This matters because the friction of publishing often determines whether a writing system actually gets used. A lower-friction path means more notes make it from private vault to public output.

### Step 4: Build and Deploy Automatically

- **Tool/Action:** GitHub Actions deploy Quartz to GitHub Pages
- **Input:** Changes pushed to the repository
- **Output:** Updated static site on GitHub Pages

With the repository and content flow in place, deployment becomes mostly automatic. GitHub Actions builds the site and GitHub Pages hosts the generated output, which means the publishing pipeline is reproducible and does not depend on a manual local export every time.

---

## Practical Benefits

This setup is appealing because it keeps the stack boring in a good way.

- Static hosting means low maintenance
- Markdown files stay portable
- The site can be version-controlled like any other project
- Obsidian remains the main writing interface
- Portfolio pages and blog posts can live in the same system

For a personal site, that is a strong trade-off: fewer moving parts, fewer platforms to manage, and less risk of getting locked into a tool that changes direction later.

---

## Reflections & Lessons Learned

> [!tip] What Went Well
> Quartz felt closest to the way I already think and write in Obsidian.
> The GitHub Pages deployment model keeps infrastructure lightweight.
> Using a sync plugin reduces the friction between drafting privately and publishing publicly.

> [!warning] What Could Be Improved
> Initial setup still assumes some comfort with Node, Git, and repository structure.
> Theme customization and content organization need deliberate planning if the site grows.
> Publishing directly from a live vault requires discipline around what should remain private versus public.

**Future Roadmap - Potential Applications**

- Add a clearer content taxonomy for projects, blog posts, and evergreen notes
- Customize the Quartz theme so the site feels more portfolio-oriented
- Create a publishing checklist for metadata, tags, and screenshots before syncing

---
