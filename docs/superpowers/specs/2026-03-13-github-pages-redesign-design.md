# W-Rowan.github.io — Full Redesign Spec

**Date:** 2026-03-13
**Status:** Approved
**Author:** Will Rowan + Claude

## Overview

Complete redesign of Will Rowan's GitHub Pages personal website. The current site uses the al-folio academic Jekyll theme with mostly placeholder/template content. The redesign keeps the al-folio framework but rewrites all content, restructures navigation, updates styling, and presents Will's full dual-career profile (computer vision researcher + film critic/filmmaker).

## Design Direction

**Clean Academic** — white background, modern sans-serif typography, generous whitespace, research-forward. Professional and elevated beyond the al-folio default. The content speaks for itself.

## Narrative Approach

**Integrated narrative with research as backbone.** The site is a github.io academic site, so research is prominent. But the film/creative work is woven throughout as the distinguishing factor — not siloed as a hobby. The dual identity is the brand.

## Site Structure

Five pages (Home + four nav items: Research, Film, Projects, CV). Fixed top navigation. No blog.

### 1. Home (`/`)

**Hero section:**
- Profile photo (circular, left-aligned)
- Name: Will Rowan
- Punchy paragraph (~3–4 sentences) capturing the dual identity. Warm, specific, no jargon. Mentions: PhD Computer Science, ICLR/ECCV publications, Berlinale Talents, virtual production with dock10.
- Rotating achievement ticker with ~9 items (see below). Implementation: CSS-only horizontal scroll animation, ~3s per item, pauses on hover. Pure CSS — no JavaScript required. Items duplicate in the DOM for seamless loop.
- Social links: GitHub, Google Scholar, LinkedIn, Email

**Rotating ticker items (contextualised for all audiences):**
1. Best Presentation — Int'l Computer Vision Summer School
2. Best Poster — ECCV 2024
3. Berlinale Talents 2025 — 1 of 200 worldwide
4. 1 of 8 critics worldwide — Berlinale Talents Press
5. Featured in Variety
6. Featured in Screen Daily
7. Published in Cineuropa
8. PXLD selected for Berlinale startup programme
9. CEO, PXLD — AI virtual production startup

**Below the hero:**
- News/announcements section (5 most recent items, scrollable). Content:
  1. Joined CVMP organising committee as Socials Chair (2026)
  2. PXLD featured in Screen Daily at the European Film Market (Feb 2026)
  3. opencall.fyi launched (2026)
  4. Best Presentation award at ICVSS, Sicily (Summer 2025)
  5. Selected for Berlinale Talents and Berlinale Talents Press 2025

### 2. Research (`/research/`)

Primary audience: academics. Secondary: film industry people wanting to understand technical credibility.

**Sections:**

**Opening paragraph** — jargon-light summary of research focus: 3D face reconstruction, generative AI, virtual production. Mention the Intelligent Face Agent concept in plain language. Name supervisors (Dr Patrik Huber, Prof Nick Pears, Prof Andrew Keeling).

**Current Work** — Research Fellow, University of York. Part of £1.8M Innovate UK project with dock10 (UK's largest television studio facility, MediaCityUK) and 2LE Media. AI-powered 3D reconstruction for real-time virtual production. Secured £20,000 grant from AI SuperConnector (Imperial College London).

**Publications** — al-folio's built-in BibTeX engine with preview images. 4 papers:
- Text2Face (ICLR 2023)
- OptiFaces / "Fake It Without Making It" (ICLR 2024)
- ECCV 2024 workshop paper (Foundation Models for 3D Humans)
- Deepfake detection paper (2022)

Note: The existing `papers.bib` has 3 entries. Update with correct metadata for all 4, sourcing from the knowledge base at `KnowledgeBase/academic/publications.md`. Add preview images for any missing papers.

**Awards & Recognition:**
- Best Presentation, International Computer Vision Summer School (ICVSS), Sicily, 2025
- Best Poster, Foundation Models for 3D Humans Workshop, ECCV, Milan, 2024
- Best Presentation Runner-Up, Reproducibility in Computer Vision Workshop, CVPR, 2023
- EPSRC Doctoral Scholarship, 2020–2024
- Highest MSc grade on record, Advanced Computer Science, University of York (84%, Distinction)
- Best Dissertation in Cohort (1 of 150), BEng Computer Science, 2019
- IBM Entrance Scholarship (3 of 150), 2016

**Academic Service:**
- Socials Chair, Conference on Visual Media Production (CVMP) — organising committee
- Symposium Chair, British Machine Vision Association (BMVA) Symposium on 3D Computer Vision, February 2025
- Graduate Teaching Assistant, Multi-Agent Interaction, University of York, 2020–2021
- Dissertation Supervisor, undergraduate projects, 2021–2022

### 3. Film (`/film/`)

Primary audience: film industry. Secondary: anyone curious about the creative side.

**Sections:**

**Festival Selections & Programmes** — each with full context:
- Berlinale Talents 2025 — 1 of 200 emerging filmmakers worldwide, Berlin International Film Festival
- Berlinale Talents Press 2025 — 1 of 8 film critics worldwide
- REAL Academy, Locarno Film Festival 2025 — filmmaker lab; directed Film Fever
- GoCritic! 2024–2025 — European criticism programme at Anifilm (Liberec, Czech Republic); wrote 3 articles for Cineuropa
- Far East Film Festival Campus, Udine 2023 — 1 of 10 young critics from Europe and Asia
- Locarno Basecamp 2023 — 1 of 200 for artistic residency
- European Forum Alpbach 2025 — scholarship recipient

**Published Criticism:**
- Cineuropa — 3 articles (Anifilm awards report, reviews of Savages and Hurikan)
- Filmhounds Magazine — interview with Radu Jude (Romanian New Wave, Golden Bear winner); Blu-ray review
- Taiwan News — interview with Kai Ko on Bad Education
- Eastern Kicks — coverage from Far East Film Festival
- BBC Radio York — regular guest on Film Hour
- Yorkshire Evening Post, Movie Marker, East Euro Flicks

**Key Interviews:** Radu Jude, Kai Ko, Tommy Wiseau, Johnnie To, Gabby Wong

**Filmmaking:**
- Film Fever (2025) — 9-minute experimental documentary. Made at REAL Academy, Locarno Film Festival. Impressionistic portrait of heat, exhaustion, and dreams. Directorial debut.
- Include 2–3 Film Fever stills from assets

**Cinema Programming:**
- York Student Cinema (2017–2023, seven years). Head Film Programmer 2021–2022.
- ~100 films/year, 300-seat venue, £12,000 annual budget
- Distributor liaison, DCP management, event programming

### 4. Projects (`/projects/`)

Card-based grid layout using al-folio's `_projects` collection + masonry. PXLD featured first at double-width (requires custom CSS: add `.grid-item.featured` class with double width). Each card has: thumbnail/logo, project name, role, description, tags, link to live site.

**Projects (in order):**

1. **PXLD** (featured, double-width) — Co-founder & CEO. University of York spinout, AI-powered virtual production. Featured in Variety (San Sebastián, 2025) and Screen Daily (Berlinale, 2026). Selected for Zinemaldia Startup Challenge and European Film Market Startup Programme. Link: pxld.ai. Use PXLD logo.

2. **Before Sunrise Tracker** — Interactive web experience mapping real-time journey through Vienna from Before Sunrise (1995), synced to Vienna time. Use screenshots from project.

3. **opencall.fyi** — Founder. Curated opportunities platform for emerging artists. Residencies, fellowships, grants across film, visual arts, criticism.

4. **Swingometer** — UK's first fully automated election forecast. Poll aggregation + Monte Carlo seat prediction. Use OG image.

5. **Foresight** — AI research intelligence platform. UCL AI Festival Hackathon 2026, 2nd place. Use logo.

6. **SpeakEU** — Technical Lead & Advisor. Gen-AI civic assistant for EU democratic participation. Alpbach IDEAS 2025–2026 (1 of 4 projects). Mentored by Prof. Alberto Alemanno. Link: speakeu.eu. Use logo.

7. **Club Alpbach London** — Scholarships Coordinator. UK chapter of European Forum Alpbach. Built the chapter website. Link: clubalpbachlondon.com.

### 5. CV (`/cv/`)

Comprehensive, structured, updated to March 2026. Uses al-folio's YAML-driven CV layout (`_data/cv.yml`). Remove/ignore `assets/json/resume.json` and clear the `jsonresume` config in `_config.yml` to avoid the dual data system conflict. Sections: Education, Experience (both RF positions + PXLD), Publications, Awards & Honours, Academic Service, Film & Criticism, Projects, Skills, Community (CVMP, Club Alpbach London, SpeakEU).

## Technical Approach

### Keep
- Jekyll build system + GitHub Pages deployment
- al-folio's publication engine (jekyll-scholar + BibTeX)
- Dark mode toggle
- Responsive layout + Bootstrap grid
- CV layout engine (YAML-driven)
- Image zoom, progress bar, masonry grid

### Change
- **Typography:** Load Inter from Google Fonts (add `<link>` in `_includes/head.html`, override font-family in `_sass/_variables.scss`). Use JetBrains Mono for code/monospace accents (already in Google Fonts link).
- **Theme colours:** Clean white/light grey, accent colour TBD during implementation (replace current purple #B509AC with something subtler)
- **Navigation:** Research / Film / Projects / CV (replacing About / CV / Publications)
- **Home page:** Complete rewrite — new hero with bio + rotating ticker
- **Research page:** Custom hybrid markdown page: hand-written narrative sections with `{% bibliography %}` tag embedded inline for the publications section. Uses `layout: page`.
- **Film page:** New custom markdown page with section headers + anchors. Festival selections as a styled list/timeline, criticism as a publication list, filmmaking section with embedded stills, cinema programming as a narrative block. Uses `layout: page`.
- **Projects page:** Card grid with real images/logos, links to live sites
- **CV data:** Complete rewrite of `_data/cv.yml`
- **Publications:** Update `_bibliography/papers.bib` with all 4 papers
- **News:** Fresh announcements
- **Images:** Copy in real assets (profile photo, project logos, Film Fever stills)
- **Social links:** Updated (GitHub, Scholar, LinkedIn, email)
- **Meta/SEO:** Updated title, description, OG tags
- **Remove:** Example/placeholder blog posts, template projects, Einstein resume data, example repositories
- **Disable blog:** Set `latest_posts.enabled: false` in `_config.yml`, disable pagination and blog archives, remove `display_tags`/`display_categories` config

## Assets to Copy In

All paths are absolute from the local machine. Base: `/Users/will/Documents/Projects/`.

- Profile photo: `Personal/W-Rowan.github.io/assets/img/profile_pic.jpg` (already in repo)
- PXLD logo: `Company/pxld/company/brand/pxld_logo.png`
- PXLD icon: `Company/pxld/frontend/public/icons/pxld_icon_black.svg`
- Foresight logo: `Personal/foresight/src/app/foresight_logo.png`
- SpeakEU logo: `Personal/SpeakEU/knowledge-base/assets/brand/SpeakEULogoDesign1.svg`
- Swingometer OG: `Personal/swingometer/public/og-image.svg`
- Film Fever stills: `Personal/film-fever-website/assets/stills/` (select 2–3 best)
- Before Sunrise screenshots: `Personal/before-sunrise-tracker/Images/` (select 2–3)
- Club Alpbach London favicon: `Personal/club-alpbach-london/website/public/favicon.svg`

## Contextualisation Rules

1. No unexplained acronyms — ICVSS, ECCV, FEFF, EFM, CVMP, BMVA all spelled out or contextualised on first use
2. Stats lead, names follow — "1 of 8 critics worldwide" before "Berlinale Talents Press"
3. Context for non-insiders — "Radu Jude (Golden Bear winner)" not just "Radu Jude"; "dock10 (UK's largest TV facility)" not just "dock10"
4. Only include achievements, not applications/submissions
5. Numerically specific always — "nearly 100 films", "300-seat venue", "£12,000 budget"

## Out of Scope

- Blog/posts section
- Festival Circuit project (not live yet)
- Prix Ars Electronica submission (not submitted)
- Custom domain setup
- Analytics integration
