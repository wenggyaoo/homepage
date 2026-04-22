# Academic Homepage Design Spec

**Date:** 2026-04-22
**Owner:** Wengyao Jiang

## Overview

A personal academic homepage for a PhD student in BioAI, deployed on GitHub Pages using a fork of the RayeRen/acad-homepage.github.io Jekyll template. The site will use the original blue-white academic style with content trimmed to three sections only.

## Repository Setup

- Fork `RayeRen/acad-homepage.github.io` to GitHub account `wenggyaoo`
- Rename repo to `wenggyaoo.github.io` for automatic GitHub Pages deployment
- Site URL: `https://wenggyaoo.github.io`
- Clone to `/Users/jiangwengyao/homepage/`

## Sections

Only three sections are kept. All other sections (News, Honors, Awards, Talks, Internships, Services) are removed entirely from `_pages/about.md`.

### About Me

Three paragraphs from personal_info.txt, verbatim:

> I am a Ph.D. student in Computer Science at the School of Computing and Data Science, The University of Hong Kong (HKU), under the supervision of Prof. Zhenqin Wu.
>
> I completed my M.S. in Health Informatics at Yale University, and I hold a B.S. in Applied Mathematics from the Xi'an Jiaotong-Liverpool University. My research interests lie at the intersection of AI for Science, bioinformatics, and computational biology, with a particular focus on foundation models for single-cell and immune repertoire analysis, scientific machine learning, and multimodal medical imaging. I am passionate about deep learning algorithms, especially large language models and neural operators for biological applications.
>
> I am always open to new collaborations and discussions. Feel free to reach out.

### Publications

Manually maintained in `_pages/about.md`. Each paper entry includes:
- Pipeline/teaser image (stored in `images/` directory)
- Paper title
- Author list
- Venue (conference or journal name)
- Optional links: paper, code, project page

No Google Scholar auto-crawl. No citation count auto-update.

### Education

- Ph.D. in Computer Science, The University of Hong Kong, 2026 - present (Supervisor: Prof. Zhenqin Wu)
- M.S. in Health Informatics, Yale University, 2024 - 2026
- B.S. in Applied Mathematics, Xi'an Jiaotong-Liverpool University, 2020 - 2024

## Configuration (`_config.yml`)

| Field | Value |
|-------|-------|
| `title` | Wengyao Jiang |
| `description` | Ph.D. student in Computer Science at HKU |
| `repository` | wenggyaoo/wenggyaoo.github.io |
| `author.name` | Wengyao Jiang |
| `author.avatar` | images/headshot.JPG |
| `author.bio` | Ph.D. student in CS @ HKU |
| `author.location` | Hong Kong |
| `author.email` | wengyao.jiang@yale.edu |
| `author.github` | wenggyaoo |
| `author.orcid` | 0000-0003-0575-1164 |
| `author.googlescholar` | (not provided, field removed) |

## Assets

- `images/headshot.JPG` — profile photo (already exists locally)
- `images/<paper-name>.png` — pipeline images per paper (user provides manually)

## Style

- Identical to original RayeRen template: blue-white academic style
- No emojis anywhere in any file
- No Google Analytics (remove or leave blank)

## What Is Removed from the Original Template

- News section
- Honors and Awards section
- Talks section
- Internships section
- Services section
- Google Scholar auto-crawl Python script and GitHub Action
- All emoji characters

## Deployment

Standard GitHub Pages deployment. Pushing to `main` branch triggers automatic build and deploy. No additional CI configuration needed beyond what the template provides.
