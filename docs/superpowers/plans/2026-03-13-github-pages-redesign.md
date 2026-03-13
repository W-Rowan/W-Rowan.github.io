# W-Rowan.github.io Redesign — Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Transform Will Rowan's GitHub Pages site from a placeholder al-folio template into a polished personal site showcasing his dual career in computer vision research and film criticism.

**Architecture:** Keep the existing Jekyll + al-folio framework. Rewrite all content pages, restyle the theme (Inter font, clean accent colour), restructure navigation to Research/Film/Projects/CV, copy in real assets from other project folders, and remove all placeholder content.

**Tech Stack:** Jekyll, al-folio theme, SCSS, Bootstrap 4, jekyll-scholar (BibTeX), GitHub Pages

**Spec:** `docs/superpowers/specs/2026-03-13-github-pages-redesign-design.md`

---

## File Map

### Files to Create
- `_pages/research.md` — Research page (publications + narrative + awards + service)
- `_pages/film.md` — Film page (festivals, criticism, filmmaking, programming)
- `_sass/_ticker.scss` — CSS for rotating achievement ticker
- `_includes/ticker.html` — Ticker HTML component
- `_projects/pxld.md` — PXLD project card
- `_projects/before-sunrise-tracker.md` — Before Sunrise Tracker project card
- `_projects/opencall.md` — opencall.fyi project card
- `_projects/swingometer.md` — Swingometer project card
- `_projects/foresight.md` — Foresight project card
- `_projects/speakeu.md` — SpeakEU project card
- `_projects/club-alpbach-london.md` — Club Alpbach London project card
- `_news/cvmp_2026.md` — CVMP news item
- `_news/screen_daily_2026.md` — Screen Daily news
- `_news/opencall_2026.md` — opencall.fyi launch
- `_news/icvss_2025.md` — ICVSS award
- `_news/berlinale_2025.md` — Berlinale Talents selection

### Files to Modify
- `_config.yml` — Navigation, social, meta, disable blog, remove jsonresume
- `_pages/about.md` — Complete rewrite (hero + ticker + bio)
- `_pages/cv.md` — Update frontmatter
- `_data/cv.yml` — Complete rewrite with all current data
- `_bibliography/papers.bib` — Update to 5 papers with correct metadata
- `_sass/_variables.scss` — New accent colour
- `_sass/_themes.scss` — Updated theme colours
- `_sass/_base.scss` — Featured project card CSS, ticker import
- `_includes/head.html` — Add Inter + JetBrains Mono font imports
- `_layouts/about.html` — Add ticker include to hero section
- `assets/css/main.scss` — Import ticker stylesheet

### Files to Delete
- `_projects/1_project.md` through `6_project.md` — Template projects
- `_news/announcement_1.md` through `announcement_8.md` + copy — Template news
- `_posts/*` — All example blog posts
- `_pages/publications.md` — Replaced by research page
- `assets/json/resume.json` — Unused JSON resume

### Assets to Copy In
- `assets/img/pxld_logo.png` ← `/Users/will/Documents/Projects/Company/pxld/company/brand/pxld_logo.png`
- `assets/img/pxld_icon.svg` ← `/Users/will/Documents/Projects/Company/pxld/frontend/public/icons/pxld_icon_black.svg`
- `assets/img/foresight_logo.png` ← `/Users/will/Documents/Projects/Personal/foresight/src/app/foresight_logo.png`
- `assets/img/speakeu_logo.svg` ← `/Users/will/Documents/Projects/Personal/SpeakEU/knowledge-base/assets/brand/SpeakEULogoDesign1.svg`
- `assets/img/swingometer_og.svg` ← `/Users/will/Documents/Projects/Personal/swingometer/public/og-image.svg`
- `assets/img/club_alpbach_london.svg` ← `/Users/will/Documents/Projects/Personal/club-alpbach-london/website/public/favicon.svg`
- `assets/img/filmfever_still_1.jpg` ← `/Users/will/Documents/Projects/Personal/film-fever-website/assets/stills/head-on-fire-pursued-by-demon.jpg`
- `assets/img/filmfever_still_2.jpg` ← `/Users/will/Documents/Projects/Personal/film-fever-website/assets/stills/cinema-rialto-daydream.jpg`
- `assets/img/filmfever_still_3.jpg` ← `/Users/will/Documents/Projects/Personal/film-fever-website/assets/stills/blinding-heat.jpg`
- `assets/img/bst_screenshot_1.jpg` ← `/Users/will/Documents/Projects/Personal/before-sunrise-tracker/Images/Film Stills/cafe_sperl.jpg`
- `assets/img/bst_screenshot_2.jpg` ← `/Users/will/Documents/Projects/Personal/before-sunrise-tracker/Images/Present Day/Zollamtssteg.png`

---

## Chunk 1: Foundation — Config, Cleanup, Styling

### Task 1: Clean up placeholder content

**Files:**
- Delete: `_projects/1_project.md` through `6_project.md`
- Delete: `_news/announcement_1.md` through `announcement_8.md` + `announcement_6.5 copy.md`
- Delete: `_pages/publications.md`
- Delete: `assets/json/resume.json`
- Delete: all files in `_posts/`

- [ ] **Step 1: Delete template project files**

```bash
rm /Users/will/Documents/Projects/Personal/W-Rowan.github.io/_projects/[1-6]_project.md
```

- [ ] **Step 2: Delete template news files**

```bash
rm /Users/will/Documents/Projects/Personal/W-Rowan.github.io/_news/announcement_*.md
```

- [ ] **Step 3: Delete template blog posts**

```bash
rm -r /Users/will/Documents/Projects/Personal/W-Rowan.github.io/_posts/*
```

- [ ] **Step 4: Delete old publications page and JSON resume**

```bash
rm /Users/will/Documents/Projects/Personal/W-Rowan.github.io/_pages/publications.md
rm /Users/will/Documents/Projects/Personal/W-Rowan.github.io/assets/json/resume.json
```

- [ ] **Step 5: Commit cleanup**

```bash
git add -A && git commit -m "chore: remove all placeholder/template content"
```

### Task 2: Update _config.yml

**Files:**
- Modify: `_config.yml`

- [ ] **Step 1: Update site metadata**

Change these fields in `_config.yml`:
- `email:` → `will.rowan@york.ac.uk`
- `description:` → `Computer vision researcher and film critic. PhD University of York.`
- `keywords:` → `computer vision, film criticism, 3D face reconstruction, virtual production, Will Rowan`
- `footer_text:` → remove the al-folio credit, use simple `© Will Rowan 2026`
- `icon:` → use a simple favicon or leave as emoji
- `serve_og_meta:` → `true`
- `serve_schema_org:` → `true`

- [ ] **Step 2: Disable blog and JSON resume**

In `_config.yml`:
- `latest_posts.enabled:` → `false`
- `pagination.enabled:` → `false`
- `related_blog_posts.enabled:` → `false`
- Remove or comment out the `display_tags` and `display_categories` lines
- Remove or comment out the `jekyll_get_json` and `jsonresume` sections (lines 398-413)
- `blog_name:` → comment out or remove
- `blog_description:` → comment out or remove

- [ ] **Step 3: Update social links**

In `_config.yml`:
- Keep: `github_username: W-Rowan`
- Keep: `linkedin_username: will-rowan`
- Keep: `scholar_userid: YHH_2uYAAAAJ`
- `x_username:` → clear (or keep `WillRowan3` if still active)
- `contact_note:` → `Most responsive on email.`

- [ ] **Step 4: Commit config updates**

```bash
git add _config.yml && git commit -m "chore: update site config — metadata, disable blog, clean social"
```

### Task 3: Update typography and theme colours

**Files:**
- Modify: `_includes/head.html`
- Modify: `_sass/_variables.scss`
- Modify: `_sass/_themes.scss`

- [ ] **Step 1: Add Inter and JetBrains Mono fonts**

In `_includes/head.html`, replace the existing Roboto Google Fonts line (line 14):
```html
<link rel="stylesheet" type="text/css" href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Roboto+Slab:100,300,400,500,700|Material+Icons">
```
With:
```html
<link rel="stylesheet" type="text/css" href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap">
<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
```

- [ ] **Step 2: Update SCSS variables**

In `_sass/_variables.scss`, change the purple accent to a professional blue-grey:
- `$purple-color: #B509AC` → `$purple-color: #2563eb` (a clean blue — variable name is legacy but controls the theme accent)
- `$cyan-color: #2698BA` → `$cyan-color: #38bdf8` (lighter blue for dark mode)

- [ ] **Step 3: Update font family in _base.scss**

Find the `body` font-family declaration in `_sass/_base.scss` and update it to use Inter:
```scss
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
```

Also find any `code, pre` font-family and set:
```scss
font-family: 'JetBrains Mono', 'Fira Code', monospace;
```

- [ ] **Step 4: Commit styling changes**

```bash
git add _includes/head.html _sass/_variables.scss _sass/_base.scss && git commit -m "style: switch to Inter font, update accent colours"
```

### Task 4: Copy in real assets

**Files:**
- Create: multiple files in `assets/img/`

- [ ] **Step 1: Copy project logos and images**

```bash
BASE="/Users/will/Documents/Projects"
DEST="/Users/will/Documents/Projects/Personal/W-Rowan.github.io/assets/img"

cp "$BASE/Company/pxld/company/brand/pxld_logo.png" "$DEST/pxld_logo.png"
cp "$BASE/Company/pxld/frontend/public/icons/pxld_icon_black.svg" "$DEST/pxld_icon.svg"
cp "$BASE/Personal/foresight/src/app/foresight_logo.png" "$DEST/foresight_logo.png"
cp "$BASE/Personal/SpeakEU/knowledge-base/assets/brand/SpeakEULogoDesign1.svg" "$DEST/speakeu_logo.svg"
cp "$BASE/Personal/swingometer/public/og-image.svg" "$DEST/swingometer_og.svg"
cp "$BASE/Personal/club-alpbach-london/website/public/favicon.svg" "$DEST/club_alpbach_london.svg"
```

- [ ] **Step 2: Copy Film Fever stills**

```bash
STILLS="$BASE/Personal/film-fever-website/assets/stills"
cp "$STILLS/head-on-fire-pursued-by-demon.jpg" "$DEST/filmfever_still_1.jpg"
cp "$STILLS/cinema-rialto-daydream.jpg" "$DEST/filmfever_still_2.jpg"
cp "$STILLS/blinding-heat.jpg" "$DEST/filmfever_still_3.jpg"
```

- [ ] **Step 3: Copy Before Sunrise Tracker images**

```bash
BST="$BASE/Personal/before-sunrise-tracker/Images"
cp "$BST/Film Stills/cafe_sperl.jpg" "$DEST/bst_screenshot_1.jpg"
cp "$BST/Present Day/Zollamtssteg.png" "$DEST/bst_screenshot_2.png"
```

- [ ] **Step 4: Commit assets**

```bash
cd /Users/will/Documents/Projects/Personal/W-Rowan.github.io
git add assets/img/ && git commit -m "assets: add project logos, Film Fever stills, BST screenshots"
```

---

## Chunk 2: Home Page — Hero, Ticker, News

### Task 5: Create the achievement ticker component

**Files:**
- Create: `_sass/_ticker.scss`
- Create: `_includes/ticker.html`
- Modify: `assets/css/main.scss`

- [ ] **Step 1: Create ticker SCSS**

Create `_sass/_ticker.scss`:
```scss
// Achievement ticker — CSS-only horizontal scroll
.achievement-ticker {
  overflow: hidden;
  background: var(--global-bg-color);
  border: 1px solid var(--global-divider-color);
  border-radius: 8px;
  padding: 8px 0;
  margin: 1.5rem 0;
  position: relative;

  &:hover .ticker-track {
    animation-play-state: paused;
  }

  .ticker-label {
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    display: flex;
    align-items: center;
    padding: 0 12px;
    background: var(--global-bg-color);
    z-index: 2;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--global-text-color-light);
    border-right: 1px solid var(--global-divider-color);
  }
}

.ticker-track {
  display: flex;
  gap: 12px;
  animation: ticker-scroll 40s linear infinite;
  width: max-content;
  padding-left: 80px; // space for label
}

.ticker-item {
  white-space: nowrap;
  padding: 4px 14px;
  background: var(--global-card-bg-color);
  border: 1px solid var(--global-divider-color);
  border-radius: 20px;
  font-size: 0.85rem;
  color: var(--global-text-color);
  flex-shrink: 0;
}

@keyframes ticker-scroll {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
```

- [ ] **Step 2: Create ticker HTML include**

Create `_includes/ticker.html`:
```html
<div class="achievement-ticker">
  <span class="ticker-label">Recent</span>
  <div class="ticker-track">
    <span class="ticker-item">Best Presentation — Int'l Computer Vision Summer School</span>
    <span class="ticker-item">Best Poster — ECCV 2024</span>
    <span class="ticker-item">Berlinale Talents 2025 — 1 of 200 worldwide</span>
    <span class="ticker-item">1 of 8 critics worldwide — Berlinale Talents Press</span>
    <span class="ticker-item">Featured in Variety</span>
    <span class="ticker-item">Featured in Screen Daily</span>
    <span class="ticker-item">Published in Cineuropa</span>
    <span class="ticker-item">PXLD selected for Berlinale startup programme</span>
    <span class="ticker-item">CEO, PXLD — AI virtual production startup</span>
    <!-- Duplicate for seamless loop -->
    <span class="ticker-item">Best Presentation — Int'l Computer Vision Summer School</span>
    <span class="ticker-item">Best Poster — ECCV 2024</span>
    <span class="ticker-item">Berlinale Talents 2025 — 1 of 200 worldwide</span>
    <span class="ticker-item">1 of 8 critics worldwide — Berlinale Talents Press</span>
    <span class="ticker-item">Featured in Variety</span>
    <span class="ticker-item">Featured in Screen Daily</span>
    <span class="ticker-item">Published in Cineuropa</span>
    <span class="ticker-item">PXLD selected for Berlinale startup programme</span>
    <span class="ticker-item">CEO, PXLD — AI virtual production startup</span>
  </div>
</div>
```

- [ ] **Step 3: Import ticker in main.scss**

In `assets/css/main.scss`, add `@import "ticker";` after existing imports.

- [ ] **Step 4: Commit ticker component**

```bash
git add _sass/_ticker.scss _includes/ticker.html assets/css/main.scss && git commit -m "feat: add CSS-only achievement ticker component"
```

### Task 6: Rewrite the home page

**Files:**
- Modify: `_pages/about.md`
- Modify: `_layouts/about.html`

- [ ] **Step 1: Add ticker include to about layout**

In `_layouts/about.html`, add the ticker include after the `{{ content }}` clearfix div and before the News section:
```html
          <div class="clearfix">
            {{ content }}
          </div>

          <!-- Achievement Ticker -->
          {% if page.ticker -%}
            {%- include ticker.html %}
          {%- endif %}

          <!-- News -->
```

- [ ] **Step 2: Rewrite about.md**

Replace the entire content of `_pages/about.md`:
```markdown
---
layout: about
title: about
permalink: /
subtitle:

profile:
  align: right
  image: profile_pic.jpg
  image_circular: true

news: true
latest_posts: false
selected_papers: false
social: true
ticker: true
---

Computer vision researcher and freelance film critic. I build intelligent systems for the human face and write about cinema that changes how we see.

PhD from the University of York, with publications at ICLR and ECCV and a Best Poster award. One of 200 filmmakers selected for Berlinale Talents 2025, and simultaneously one of 8 critics worldwide for Talents Press. Currently developing AI-powered virtual production tools with [dock10](https://www.dock10.co.uk) (the UK's largest television studio facility) as part of a £1.8M Innovate UK project, and co-founder of [PXLD](https://pxld.ai), a virtual production startup featured in Variety and Screen Daily.

I have never met another computer vision researcher at a film festival. That is the space I work in.
```

- [ ] **Step 3: Commit home page**

```bash
git add _pages/about.md _layouts/about.html && git commit -m "feat: rewrite home page — punchy bio, circular photo, ticker"
```

### Task 7: Create fresh news announcements

**Files:**
- Create: 5 new files in `_news/`

- [ ] **Step 1: Create all news items**

Create `_news/cvmp_2026.md`:
```markdown
---
layout: post
date: 2026-03-01 09:00:00+0000
inline: true
related_posts: false
---

Joined the organising committee for the **Conference on Visual Media Production (CVMP)** as Socials Chair.
```

Create `_news/screen_daily_2026.md`:
```markdown
---
layout: post
date: 2026-02-20 09:00:00+0000
inline: true
related_posts: false
---

**PXLD** featured in **Screen Daily** at the European Film Market during the Berlinale.
```

Create `_news/opencall_2026.md`:
```markdown
---
layout: post
date: 2026-01-15 09:00:00+0000
inline: true
related_posts: false
---

Launched **[opencall.fyi](https://opencall.fyi)**, a curated platform helping emerging artists discover residencies, fellowships, grants, and competitions.
```

Create `_news/icvss_2025.md`:
```markdown
---
layout: post
date: 2025-07-15 09:00:00+0000
inline: true
related_posts: false
---

Awarded **Best Presentation** at the International Computer Vision Summer School (ICVSS) in Sicily.
```

Create `_news/berlinale_2025.md`:
```markdown
---
layout: post
date: 2025-02-15 09:00:00+0000
inline: true
related_posts: false
---

Selected for **Berlinale Talents 2025** (1 of 200 worldwide) and **Berlinale Talents Press** (1 of 8 film critics worldwide) at the Berlin International Film Festival.
```

- [ ] **Step 2: Commit news items**

```bash
git add _news/ && git commit -m "feat: add 5 fresh news announcements (2025-2026)"
```

---

## Chunk 3: Research Page and Publications

### Task 8: Update publications BibTeX

**Files:**
- Modify: `_bibliography/papers.bib`

- [ ] **Step 1: Rewrite papers.bib with all 5 papers**

Replace entire contents of `_bibliography/papers.bib`:
```bibtex
---
---

@inproceedings{rowan2024nheads,
  bibtex_show={true},
  title={N Heads Are Better Than One: Exploring Theoretical Performance Bounds of 3D Face Reconstruction Methods},
  author={Rowan, Will and Huber, Patrik and Pears, Nick and Keeling, Andrew},
  booktitle={ECCV Workshop on Foundation Models for 3D Humans},
  year={2024},
  preview={NHeadsTeaserWeb.png},
  abstract={We explore upper bounds on 3D face reconstruction accuracy using multiple views and establish benchmarks for single-view methods.},
  selected={true}
}

@inproceedings{rowan2024optifaces,
  bibtex_show={true},
  title={How Many OptiFaces? A New Evaluation Metric for 3D Face Reconstruction},
  author={Rowan, Will and Huber, Patrik and Pears, Nick and Keeling, Andrew},
  booktitle={International Conference on Learning Representations (ICLR)},
  year={2024},
  html={https://openreview.net/forum?id=yourID},
  preview={FIWMITeaserWeb.png},
  abstract={We propose OptiFaces, a new evaluation metric that addresses limitations of existing 3D face reconstruction benchmarks.},
  abbr={ICLR},
  selected={true}
}

@inproceedings{rowan2023text2face,
  bibtex_show={true},
  title={Text2Face: 3D Morphable Faces from Text},
  author={Rowan, Will and Huber, Patrik and Pears, Nick and Keeling, Andrew},
  booktitle={International Conference on Learning Representations (ICLR)},
  html={https://openreview.net/pdf?id=7Zyv70nGl_g},
  doi={10.48550/arXiv.2303.02688},
  year={2023},
  preview={Text2FaceTeaserWeb.png},
  abstract={We present Text2Face, the first method for generating 3D face shape from text descriptions using a 3D Morphable Model.},
  abbr={ICLR},
  selected={true}
}

@inproceedings{sanvitale2024,
  bibtex_show={true},
  title={San Vitale Challenge: Automatic Reconstruction of Ancient Colored Glass Windows},
  author={Di Domenico, Nicolo and Borghi, Guido and Franco, Annalisa and Rowan, Will and others},
  booktitle={ECCV Workshop on Artificial Intelligence for Digital Humanities},
  year={2024},
  preview={SanVitaleTeaserWeb.png}
}

@article{rowan2022deepfake,
  bibtex_show={true},
  title={The Effectiveness of Temporal Dependency in Deepfake Video Detection},
  author={Rowan, Will and Pears, Nick},
  journal={arXiv preprint arXiv:2205.06684},
  html={https://arxiv.org/pdf/2205.06684.pdf},
  preview={DeepfakeTeaserWeb.png},
  year={2022}
}
```

Note: The implementer should verify the OpenReview URL for the OptiFaces paper and add correct links. Preview images for new papers (NHeadsTeaserWeb.png, SanVitaleTeaserWeb.png) need to be created or sourced — use placeholder text images if originals are unavailable.

- [ ] **Step 2: Commit updated bibliography**

```bash
git add _bibliography/papers.bib && git commit -m "feat: update publications — 5 papers with correct venues and metadata"
```

### Task 9: Create the Research page

**Files:**
- Create: `_pages/research.md`

- [ ] **Step 1: Write research.md**

Create `_pages/research.md`:
```markdown
---
layout: page
title: research
permalink: /research/
description: Computer vision, 3D face reconstruction, generative AI, and virtual production.
nav: true
nav_order: 1
---

My research focuses on building intelligent systems for the human face: methods that can take any input — text, a photo, a partial 3D scan — and produce an accurate, editable 3D model. I call this the Intelligent Face Agent.

My PhD thesis, *"Towards an Intelligent Agent for the Human Face"*, introduced new approaches to 3D face reconstruction, text-driven face generation, and evaluation metrics for the field. I was supervised by [Dr Patrik Huber](https://www.patrikhuber.ch), [Prof Nick Pears](https://www.cs.york.ac.uk/people/?group=Academic%20and%20Teaching%20Staff&username=nep), and [Prof Andrew Keeling](https://medicinehealth.leeds.ac.uk/dentistry/staff/492/professor-andrew-keeling) at the University of York.

## Current Work

I am a Research Fellow in the Department of Computer Science at the University of York, working on a **£1.8M Innovate UK project** with [dock10](https://www.dock10.co.uk) (the UK's largest television studio facility, based at MediaCityUK) and 2LE Media. We are developing AI-powered 3D reconstruction techniques for real-time virtual production compositing — allowing actors to be seamlessly placed into virtual environments during live broadcast.

I also secured a **£20,000 grant** from the AI SuperConnector startup accelerator at Imperial College London, and pitched and organised the workshop *"Capturing Reality and Changing It"* at the 2024 Locarno Film Festival.

## Publications

<div class="publications">
{% bibliography -f papers %}
</div>

## Awards & Recognition

- **Best Presentation**, International Computer Vision Summer School (ICVSS), Sicily, 2025
- **Best Poster**, Foundation Models for 3D Humans Workshop, European Conference on Computer Vision (ECCV), Milan, 2024
- **Best Presentation Runner-Up**, Reproducibility in Computer Vision Workshop, CVPR, 2023
- **EPSRC Doctoral Scholarship**, 2020–2024
- **Highest MSc grade on record**, Advanced Computer Science, University of York (84%, Distinction)
- **Best Dissertation in Cohort** (1 of 150), BEng Computer Science, University of York, 2019
- **IBM Entrance Scholarship** (3 of 150), University of York, 2016

## Academic Service

- **Socials Chair**, [Conference on Visual Media Production (CVMP)](https://www.cvmp-conference.org) — organising committee
- **Symposium Chair**, British Machine Vision Association (BMVA) Symposium on 3D Computer Vision, February 2025
- **Graduate Teaching Assistant**, Multi-Agent Interaction, University of York, 2020–2021 (40 students)
- **Dissertation Supervisor**, undergraduate projects, University of York, 2021–2022
```

- [ ] **Step 2: Commit research page**

```bash
git add _pages/research.md && git commit -m "feat: add Research page — publications, awards, service, current work"
```

---

## Chunk 4: Film Page

### Task 10: Create the Film page

**Files:**
- Create: `_pages/film.md`

- [ ] **Step 1: Write film.md**

Create `_pages/film.md`:
```markdown
---
layout: page
title: film
permalink: /film/
description: Criticism, festivals, filmmaking, and cinema programming.
nav: true
nav_order: 2
---

## Festival Selections & Programmes

- **Berlinale Talents 2025** — selected as 1 of 200 emerging filmmakers from thousands of applicants worldwide, at the Berlin International Film Festival
- **Berlinale Talents Press 2025** — simultaneously selected as 1 of 8 film critics worldwide for the dedicated press programme
- **REAL Academy, Locarno Film Festival 2025** — selected for the festival's filmmaker lab; directed *Film Fever* (see below)
- **GoCritic! 2024–2025** — selected for the European film criticism programme at Anifilm (Liberec, Czech Republic); wrote three articles for [Cineuropa](https://www.cineuropa.org), Europe's leading film industry publication
- **Far East Film Festival Campus, Udine 2023** — selected as 1 of 10 young critics from Europe and Asia
- **Locarno Basecamp 2023** — selected as 1 of 200 for the Locarno Film Festival's artistic residency
- **European Forum Alpbach 2025** — scholarship recipient

## Published Criticism

- **[Cineuropa](https://www.cineuropa.org)** — 3 articles: Anifilm awards report, reviews of *Savages* (Claude Barras) and *Hurikan* (Jan Saska)
- **[Filmhounds Magazine](https://www.filmhounds.co.uk)** — interview with Radu Jude (Romanian New Wave director, Golden Bear winner); *Yes Madam* Blu-ray review
- **Taiwan News** — interview with Kai Ko on *Bad Education*
- **Eastern Kicks** — coverage from the Far East Film Festival
- **BBC Radio York** — regular guest on the Film Hour
- **Yorkshire Evening Post**, **Movie Marker**, **East Euro Flicks**

### Interviews

Published interviews with **Radu Jude**, **Kai Ko**, **Tommy Wiseau**, **Johnnie To**, and **Gabby Wong**.

## Filmmaking

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/filmfever_still_1.jpg" title="Film Fever still" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/filmfever_still_2.jpg" title="Film Fever still" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/filmfever_still_3.jpg" title="Film Fever still" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Stills from <em>Film Fever</em> (2025).
</div>

**Film Fever** (2025) — a 9-minute experimental documentary made during the REAL Academy at the Locarno Film Festival. An impressionistic portrait of heat, exhaustion, and dreams at a film festival, built from cross-dissolves and non-linear structure. Directorial debut.

## Cinema Programming

**York Student Cinema** (2017–2023, seven years). I was Head Film Programmer in 2021–2022, curating nearly 100 films per year for a 300-seat student-run venue with a £12,000 annual budget. The role involved distributor liaison, DCP ordering, scheduling, flyer design, and event programming — from *Rocky Horror Picture Show* midnight screenings to *The Room* with Tommy Wiseau in attendance.

I started selling popcorn at the cinema in my first year of university in 2017, and by 2021 I was choosing every film that played on screen. It remains one of the roles I am most proud of.
```

- [ ] **Step 2: Commit Film page**

```bash
git add _pages/film.md && git commit -m "feat: add Film page — festivals, criticism, filmmaking, programming"
```

---

## Chunk 5: Projects Page

### Task 11: Create all project card files

**Files:**
- Create: 7 files in `_projects/`

- [ ] **Step 1: Create PXLD project (featured)**

Create `_projects/pxld.md`:
```markdown
---
layout: page
title: PXLD
description: "Co-founder & CEO. University of York spinout building AI-powered virtual production tools. Featured in Variety and Screen Daily."
img: assets/img/pxld_logo.png
importance: 1
category: ventures
redirect: https://pxld.ai
---
```

- [ ] **Step 2: Create Before Sunrise Tracker project**

Create `_projects/before-sunrise-tracker.md`:
```markdown
---
layout: page
title: Before Sunrise Tracker
description: "Interactive web experience mapping the real-time journey of Céline and Jesse through Vienna in Before Sunrise (1995), synchronised to Vienna time."
img: assets/img/bst_screenshot_1.jpg
importance: 2
category: creative
redirect: https://beforesunrisetracker.com
---
```

- [ ] **Step 3: Create opencall.fyi project**

Create `_projects/opencall.md`:
```markdown
---
layout: page
title: opencall.fyi
description: "Founder. Curated opportunities platform helping emerging artists discover residencies, fellowships, grants, and competitions."
img:
importance: 3
category: ventures
redirect: https://opencall.fyi
---
```

- [ ] **Step 4: Create Swingometer project**

Create `_projects/swingometer.md`:
```markdown
---
layout: page
title: Swingometer
description: "The UK's first fully automated election forecast platform. Poll aggregation and Monte Carlo seat prediction."
img: assets/img/swingometer_og.svg
importance: 4
category: tech
redirect: https://swingometer.co.uk
---
```

Note: Verify the Swingometer URL is correct.

- [ ] **Step 5: Create Foresight project**

Create `_projects/foresight.md`:
```markdown
---
layout: page
title: Foresight
description: "AI research intelligence platform with interactive timeline visualisation. 2nd place, UCL AI Festival Hackathon 2026."
img: assets/img/foresight_logo.png
importance: 5
category: tech
---
```

- [ ] **Step 6: Create SpeakEU project**

Create `_projects/speakeu.md`:
```markdown
---
layout: page
title: SpeakEU
description: "Technical Lead & Advisor. Gen-AI civic assistant for EU democratic participation. Alpbach IDEAS 2025–2026 (1 of 4 projects)."
img: assets/img/speakeu_logo.svg
importance: 6
category: civic
redirect: https://speakeu.eu
---
```

- [ ] **Step 7: Create Club Alpbach London project**

Create `_projects/club-alpbach-london.md`:
```markdown
---
layout: page
title: Club Alpbach London
description: "Scholarships Coordinator. UK chapter of the European Forum Alpbach, connecting young people with fully-funded scholarships."
img: assets/img/club_alpbach_london.svg
importance: 7
category: civic
redirect: https://www.clubalpbachlondon.com
---
```

- [ ] **Step 8: Add featured project CSS**

In `_sass/_base.scss`, find the `.grid-item` styles and add after them:
```scss
.grid-item.grid-item-featured {
  width: 540px;
  @media (max-width: 768px) {
    width: 100%;
  }
}
```

Also update `_includes/projects.html` (if needed) to add the `grid-item-featured` class to the first/most important project. Check how al-folio renders projects and add a conditional class based on a `featured` frontmatter field. If this is complex, skip the double-width and just ensure PXLD appears first (which `importance: 1` already handles).

- [ ] **Step 9: Commit all projects**

```bash
git add _projects/ _sass/_base.scss && git commit -m "feat: add 7 project cards with real logos and descriptions"
```

---

## Chunk 6: CV Data and Final Config

### Task 12: Rewrite CV data

**Files:**
- Modify: `_data/cv.yml`

- [ ] **Step 1: Write complete cv.yml**

Replace entire contents of `_data/cv.yml`:
```yaml
- title: General Information
  type: map
  contents:
    - name: Name
      value: Will Rowan
    - name: Email
      value: will.rowan@york.ac.uk
    - name: Website
      value: w-rowan.github.io
    - name: Location
      value: York, United Kingdom
    - name: Nationality
      value: British / Irish

- title: Education
  type: time_table
  contents:
    - title: PhD Computer Science
      institution: University of York
      year: 2020–2025
      description:
        - "<strong>Thesis:</strong> Towards an Intelligent Agent for the Human Face: Improving the Accuracy, Controllability, and Explainability of 3D Face Reconstruction"
        - "<strong>Supervisors:</strong> Dr Patrik Huber, Prof Nick Pears, Prof Andrew Keeling"
        - "Viva passed 2025. EPSRC Doctoral Scholarship."
    - title: MSc Advanced Computer Science
      institution: University of York
      year: 2019–2020
      description:
        - "<strong>Grade:</strong> Distinction, 84% (highest on record)"
        - "<strong>Thesis:</strong> The Effect of Temporal Dependency in Deepfake Detection"
    - title: BEng Computer Science
      institution: University of York
      year: 2016–2019
      description:
        - "<strong>Grade:</strong> First with Distinction, 85%"
        - "<strong>Thesis:</strong> Deep Learning for Gaze Estimation (best dissertation in cohort, 1 of 150)"

- title: Experience
  type: time_table
  contents:
    - title: Co-founder & CEO
      institution: PXLD (University of York spinout)
      year: 2024–present
      description:
        - "AI-powered virtual production startup. Featured in Variety and Screen Daily."
        - "Selected for Zinemaldia Startup Challenge (San Sebastián) and European Film Market Startup Programme (Berlinale)."
    - title: Research Fellow, Computer Science
      institution: University of York
      year: 2025–2026
      description:
        - "£1.8M Innovate UK project with dock10 (UK's largest TV facility) and 2LE Media."
        - "Developing AI-powered 3D reconstruction for real-time virtual production compositing."
        - "Secured £20,000 grant from AI SuperConnector (Imperial College London)."
    - title: Research Fellow, Arts & Creative Technologies
      institution: University of York
      year: 2024–2025
      description:
        - "Virtual production research. Organised workshop at 2024 Locarno Film Festival."
    - title: Graduate Teaching Assistant
      institution: University of York
      year: 2020–2021
      description:
        - "Multi-Agent Interaction module (40 students). Dissertation supervisor 2021–2022."

- title: Publications
  type: list
  contents:
    - "<strong>N Heads Are Better Than One</strong> — ECCV Workshop on Foundation Models for 3D Humans (2024). <strong>Best Poster Award.</strong>"
    - "<strong>How Many OptiFaces?</strong> — ICLR (2024)"
    - "<strong>Text2Face: 3D Morphable Faces from Text</strong> — ICLR (2023)"
    - "<strong>San Vitale Challenge</strong> — ECCV Workshop on AI for Digital Humanities (2024)"
    - "<strong>Temporal Dependency in Deepfake Detection</strong> — arXiv (2022)"

- title: Awards & Honours
  type: time_table
  contents:
    - year: 2025
      items:
        - "<strong>Best Presentation</strong>, International Computer Vision Summer School (ICVSS), Sicily"
        - "<strong>Berlinale Talents</strong> (1 of 200 worldwide), Berlin International Film Festival"
        - "<strong>Berlinale Talents Press</strong> (1 of 8 film critics worldwide)"
        - "<strong>REAL Academy</strong>, Locarno Film Festival — filmmaker lab"
        - "<strong>European Forum Alpbach</strong> — scholarship recipient"
    - year: 2024
      items:
        - "<strong>Best Poster</strong>, Foundation Models for 3D Humans Workshop, ECCV, Milan"
        - "<strong>GoCritic!</strong> — European criticism programme; wrote for Cineuropa"
    - year: 2023
      items:
        - "<strong>Best Presentation Runner-Up</strong>, Reproducibility in Computer Vision, CVPR"
        - "<strong>Far East Film Festival Campus</strong> (1 of 10 from Europe & Asia), Udine"
        - "<strong>Locarno Basecamp</strong> (1 of 200 worldwide), Locarno Film Festival"
    - year: 2020
      items:
        - "<strong>EPSRC Doctoral Scholarship</strong>"
        - "<strong>Writer of the Year</strong> (1 of 20,000), University of York"
    - year: 2019
      items:
        - "<strong>Best Dissertation in Cohort</strong> (1 of 150), BEng Computer Science"
    - year: 2016
      items:
        - "<strong>IBM Entrance Scholarship</strong> (3 of 150), University of York"

- title: Film & Criticism
  type: nested_list
  contents:
    - title: Published Criticism
      items:
        - "Cineuropa, Filmhounds Magazine, Taiwan News, Eastern Kicks, BBC Radio York, Yorkshire Evening Post, Movie Marker, East Euro Flicks"
    - title: Key Interviews
      items:
        - "Radu Jude, Kai Ko, Tommy Wiseau, Johnnie To, Gabby Wong"
    - title: Filmmaking
      items:
        - "<em>Film Fever</em> (2025) — 9-min experimental documentary, REAL Academy, Locarno Film Festival"
    - title: Cinema Programming
      items:
        - "York Student Cinema (2017–2023). Head Film Programmer 2021–2022: ~100 films/year, 300-seat venue, £12,000 budget"

- title: Academic Service
  type: list
  contents:
    - "<strong>Socials Chair</strong>, Conference on Visual Media Production (CVMP) — organising committee"
    - "<strong>Symposium Chair</strong>, BMVA Symposium on 3D Computer Vision, February 2025"

- title: Projects & Ventures
  type: nested_list
  contents:
    - title: PXLD
      items:
        - "Co-founder & CEO. AI-powered virtual production. pxld.ai"
    - title: opencall.fyi
      items:
        - "Founder. Curated opportunities for emerging artists."
    - title: SpeakEU
      items:
        - "Technical Lead & Advisor. EU civic participation AI. Alpbach IDEAS 2025–2026."
    - title: Club Alpbach London
      items:
        - "Scholarships Coordinator. European Forum Alpbach UK chapter."
    - title: Before Sunrise Tracker
      items:
        - "Interactive web experience. beforesunrisetracker.com"
    - title: Swingometer
      items:
        - "UK election forecast platform."
    - title: Foresight
      items:
        - "AI research intelligence. 2nd place, UCL AI Festival Hackathon 2026."

- title: Skills
  type: nested_list
  contents:
    - title: Deep Learning
      items:
        - "PyTorch, PyTorch 3D, Keras, Transformers, Diffusers, nerfstudio"
    - title: Computer Vision
      items:
        - "OpenCV, skimage, COLMAP, MeshLab"
    - title: Data Science
      items:
        - "NumPy, Pandas, SciPy, scikit-learn, seaborn"
    - title: Software & Tools
      items:
        - "Python, Git, MATLAB, LaTeX, Docker"
    - title: Languages
      items:
        - "English (native), German (learning)"

- title: Community
  type: list
  contents:
    - "Board Member, Club Alpbach London"
    - "Advisor, SpeakEU"
    - "Editor, York Vision (2021–2022) — 30 staff, five 32-page print editions/year"
    - "Editor/President, The Lemon Press — UK's largest volunteer-run satire magazine"
```

- [ ] **Step 2: Commit CV data**

```bash
git add _data/cv.yml && git commit -m "feat: complete CV rewrite — education, experience, awards, film, projects, skills"
```

### Task 13: Final navigation and config cleanup

**Files:**
- Modify: `_config.yml` (nav order already handled by page frontmatter)
- Modify: `_pages/cv.md`

- [ ] **Step 1: Update CV page frontmatter**

Update `_pages/cv.md` to set correct nav order:
```markdown
---
layout: cv
permalink: /cv/
title: cv
nav: true
nav_order: 4
toc:
  sidebar: left
---
```

- [ ] **Step 2: Verify navigation order**

All pages should have these nav_order values:
- `research.md`: `nav_order: 1`
- `film.md`: `nav_order: 2`
- `projects` collection: handled by `_config.yml` (already has `projects` collection; the projects index page needs adding if it doesn't exist auto-generate)

Check if al-folio auto-generates a `/projects/` index. If not, we may need a `_pages/projects.md`:
```markdown
---
layout: page
title: projects
permalink: /projects/
description:
nav: true
nav_order: 3
---
```

al-folio does NOT auto-generate a projects index — the collection just defines individual project pages. A `_pages/projects.md` with the `page` layout will need the project grid included. Check how the theme's example handles this — there may be an existing include or the layout needs to iterate over `site.projects`.

- [ ] **Step 3: Create projects index page if needed**

If there's no auto-generated projects page, create `_pages/projects.md`:
```markdown
---
layout: page
title: projects
permalink: /projects/
description: Things I've built — startups, platforms, creative works, and civic tech.
nav: true
nav_order: 3
horizontal: false
---
```

(The `page` layout with projects collection should display the masonry grid. If it doesn't, use the dedicated projects layout or include `{% include projects.html %}` in the content.)

- [ ] **Step 4: Final config adjustments**

In `_config.yml`, ensure `enable_project_categories: true` so categories display properly.

- [ ] **Step 5: Commit final navigation**

```bash
git add _pages/ _config.yml && git commit -m "feat: final navigation — Research, Film, Projects, CV ordering"
```

---

## Chunk 7: Visual Verification and Polish

### Task 14: Build and verify locally

- [ ] **Step 1: Install dependencies and build**

```bash
cd /Users/will/Documents/Projects/Personal/W-Rowan.github.io
bundle install
bundle exec jekyll serve
```

Open `http://localhost:4000` and verify:

- [ ] **Step 2: Verify home page**
- Profile photo displays circular
- Bio text is correct and well-formatted
- Achievement ticker scrolls smoothly and pauses on hover
- News section shows 5 items in correct order
- Social links work (GitHub, Scholar, LinkedIn, email)
- Navigation shows: Research / Film / Projects / CV

- [ ] **Step 3: Verify Research page**
- Opening paragraph renders correctly
- Publications display via BibTeX with preview thumbnails
- Awards list is complete and properly formatted
- Academic service section present

- [ ] **Step 4: Verify Film page**
- Festival selections all display with full context
- Film Fever stills render in 3-column grid
- Published criticism list complete
- Cinema programming narrative reads well

- [ ] **Step 5: Verify Projects page**
- All 7 project cards appear with correct images/logos
- PXLD is first (importance: 1)
- External links open correctly
- Cards responsive on mobile

- [ ] **Step 6: Verify CV page**
- All sections render (Education, Experience, Publications, Awards, Film, Service, Projects, Skills, Community)
- Table of contents sidebar works
- No broken formatting

- [ ] **Step 7: Verify dark mode**
- Toggle dark mode and check all pages
- Ticker, cards, and images display correctly in both modes

- [ ] **Step 8: Fix any issues found during verification**

Address any rendering, styling, or content issues discovered.

- [ ] **Step 9: Final commit**

```bash
git add -A && git commit -m "polish: fixes from visual verification"
```

### Task 15: Push to GitHub

- [ ] **Step 1: Verify git status is clean**

```bash
git status
```

- [ ] **Step 2: Push to origin**

```bash
git push origin main
```

(Or whatever the default branch is — check with `git branch`.)

- [ ] **Step 3: Verify live site**

Wait 2–3 minutes for GitHub Pages to build, then check https://w-rowan.github.io to verify the live deployment.
