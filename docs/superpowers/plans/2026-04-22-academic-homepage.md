# Academic Homepage Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build Wengyao Jiang's personal academic homepage by forking the RayeRen template, stripping it to About Me / Publications / Education, and filling in her personal information.

**Architecture:** Clone RayeRen/acad-homepage.github.io into /Users/jiangwengyao/homepage/, replace all template content with Wengyao's info, remove unused sections and Google Scholar automation, then push to wenggyaoo/wenggyaoo.github.io for GitHub Pages deployment.

**Tech Stack:** Jekyll, SCSS, GitHub Pages. No testing framework — verification is done via `bundle exec jekyll serve` and visual inspection.

---

## File Map

| File | Action | Purpose |
|------|--------|---------|
| `/Users/jiangwengyao/homepage/` | Populate | Receive cloned template files |
| `_config.yml` | Modify | Personal info, remove jemoji, fix repo/title |
| `_pages/about.md` | Rewrite | Wengyao's bio, placeholder publication, education |
| `images/headshot.JPG` | Move | Profile photo (already at repo root, move to images/) |
| `.github/workflows/google_scholar_crawler.yaml` | Delete | Not using Google Scholar automation |
| `google_scholar_crawler/` | Delete | Not using Google Scholar automation |

---

### Task 1: Clone template into homepage directory

**Files:**
- Populate: `/Users/jiangwengyao/homepage/`

- [ ] **Step 1: Clone the template shallowly to a temp directory**

```bash
git clone --depth 1 https://github.com/RayeRen/acad-homepage.github.io /tmp/acad-template
```

Expected output: `Cloning into '/tmp/acad-template'...` then `done.`

- [ ] **Step 2: Copy template files into homepage (exclude .git)**

```bash
rsync -av --exclude='.git' /tmp/acad-template/ /Users/jiangwengyao/homepage/
```

Expected: files copied, `headshot.JPG` and `personal_info.txt` remain at root, `docs/` folder preserved.

- [ ] **Step 3: Verify key files exist**

```bash
ls /Users/jiangwengyao/homepage/_config.yml /Users/jiangwengyao/homepage/_pages/about.md /Users/jiangwengyao/homepage/images/ /Users/jiangwengyao/homepage/headshot.JPG
```

Expected: all four paths print without error.

- [ ] **Step 4: Initialize a fresh git repository**

```bash
cd /Users/jiangwengyao/homepage && git init && git add . && git commit -m "feat: initial template from RayeRen/acad-homepage.github.io"
```

Expected: `[main (root-commit) xxxxxxx] feat: initial template`

---

### Task 2: Update `_config.yml` with personal information

**Files:**
- Modify: `_config.yml`

- [ ] **Step 1: Replace the Site Settings block**

In `_config.yml`, replace:
```yaml
title                    : "Lorem ipsum"
description              : "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. "
repository               : "RayeRen/acad-homepage.github.io"
google_scholar_stats_use_cdn : true
```

With:
```yaml
title                    : "Wengyao Jiang"
description              : "Ph.D. student in Computer Science at HKU"
repository               : "wenggyaoo/wenggyaoo.github.io"
google_scholar_stats_use_cdn : false
```

- [ ] **Step 2: Replace the author block**

In `_config.yml`, replace the entire `author:` block with:
```yaml
author:
  name             : "Wengyao Jiang"
  avatar           : "images/headshot.JPG"
  bio              : "Ph.D. student in CS @ HKU"
  location         : "Hong Kong"
  employer         :
  pubmed           :
  googlescholar    :
  email            : "wengyao.jiang@yale.edu"
  researchgate     :
  uri              :
  bitbucket        :
  codepen          :
  dribbble         :
  flickr           :
  facebook         :
  foursquare       :
  github           : "wenggyaoo"
  google_plus      :
  keybase          :
  instagram        :
  impactstory      :
  lastfm           :
  linkedin         :
  dblp             :
  orcid            : "https://orcid.org/0000-0003-0575-1164"
  pinterest        :
  soundcloud       :
  stackoverflow    :
  steam            :
  tumblr           :
  twitter          :
  vine             :
  weibo            :
  xing             :
  youtube          :
  wikipedia        :
```

- [ ] **Step 3: Remove jemoji from the plugins list**

In `_config.yml`, find the `plugins:` block and remove the `- jemoji` line if present. The final plugins block should be:
```yaml
plugins:
  - jekyll-paginate
  - jekyll-sitemap
  - jekyll-gist
  - jekyll-feed
  - jekyll-redirect-from
```

- [ ] **Step 4: Fix timezone**

Replace:
```yaml
timezone: Asia/Shanghai
```
With:
```yaml
timezone: Asia/Hong_Kong
```

- [ ] **Step 5: Verify no Lorem ipsum remains in _config.yml**

```bash
grep -i "lorem\|ipsum\|RayeRen\|YOUR_GOOGLE" /Users/jiangwengyao/homepage/_config.yml
```

Expected: no output.

- [ ] **Step 6: Commit**

```bash
cd /Users/jiangwengyao/homepage && git add _config.yml && git commit -m "feat: configure personal info in _config.yml"
```

---

### Task 3: Rewrite `_pages/about.md`

**Files:**
- Rewrite: `_pages/about.md`

- [ ] **Step 1: Replace the entire file with Wengyao's content**

Write the following as the complete content of `_pages/about.md`:

```markdown
---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

<span class='anchor' id='about-me'></span>

I am a Ph.D. student in Computer Science at the School of Computing and Data Science, The University of Hong Kong (HKU), under the supervision of Prof. Zhenqin Wu.

I completed my M.S. in Health Informatics at Yale University, and I hold a B.S. in Applied Mathematics from the Xi'an Jiaotong-Liverpool University. My research interests lie at the intersection of AI for Science, bioinformatics, and computational biology, with a particular focus on foundation models for single-cell and immune repertoire analysis, scientific machine learning, and multimodal medical imaging. I am passionate about deep learning algorithms, especially large language models and neural operators for biological applications.

I am always open to new collaborations and discussions. Feel free to reach out.

# Publications

<div class='paper-box'><div class='paper-box-image'><div><div class="badge">Venue Year</div><img src='images/paper_placeholder.png' alt="paper" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

[Paper Title](https://arxiv.org)

**Wengyao Jiang**, Author 2, Author 3

*Journal/Conference Name, Year*

[**Paper**](https://arxiv.org) \| [**Code**](https://github.com/wenggyaoo)
</div>
</div>

# Education

- *2026 - present*, Ph.D. in Computer Science, The University of Hong Kong (Supervisor: Prof. Zhenqin Wu)
- *2024 - 2026*, M.S. in Health Informatics, Yale University
- *2020 - 2024*, B.S. in Applied Mathematics, Xi'an Jiaotong-Liverpool University
```

- [ ] **Step 2: Verify no emojis remain in about.md**

```bash
grep -P "[\x{1F300}-\x{1FFFF}]|\xF0[\x90-\xBF][\x80-\xBF]{2}|\xEE[\x80-\xBF][\x80-\xBF]|\xEF[\x80-\xBF][\x80-\xBF]" /Users/jiangwengyao/homepage/_pages/about.md
```

Expected: no output.

- [ ] **Step 3: Verify no Lorem ipsum or placeholder names remain**

```bash
grep -i "lorem\|ipsum\|kaiming\|YOUR_" /Users/jiangwengyao/homepage/_pages/about.md
```

Expected: no output.

- [ ] **Step 4: Commit**

```bash
cd /Users/jiangwengyao/homepage && git add _pages/about.md && git commit -m "feat: rewrite about.md with Wengyao's bio, publications placeholder, education"
```

---

### Task 4: Move headshot image to images directory

**Files:**
- Move: `headshot.JPG` → `images/headshot.JPG`

- [ ] **Step 1: Copy headshot into the images directory**

```bash
cp /Users/jiangwengyao/homepage/headshot.JPG /Users/jiangwengyao/homepage/images/headshot.JPG
```

- [ ] **Step 2: Verify the file is in place**

```bash
ls -lh /Users/jiangwengyao/homepage/images/headshot.JPG
```

Expected: file listed with non-zero size.

- [ ] **Step 3: Commit**

```bash
cd /Users/jiangwengyao/homepage && git add images/headshot.JPG && git commit -m "feat: add profile headshot"
```

---

### Task 5: Remove Google Scholar automation

**Files:**
- Delete: `.github/workflows/google_scholar_crawler.yaml`
- Delete: `google_scholar_crawler/` directory

- [ ] **Step 1: Delete the GitHub Action workflow**

```bash
rm /Users/jiangwengyao/homepage/.github/workflows/google_scholar_crawler.yaml
```

- [ ] **Step 2: Delete the Google Scholar crawler directory**

```bash
rm -rf /Users/jiangwengyao/homepage/google_scholar_crawler
```

- [ ] **Step 3: Check if google-scholar-stats directory exists and delete it**

```bash
rm -rf /Users/jiangwengyao/homepage/google-scholar-stats 2>/dev/null; echo "done"
```

Expected: `done`

- [ ] **Step 4: Commit**

```bash
cd /Users/jiangwengyao/homepage && git add -A && git commit -m "chore: remove Google Scholar crawler and automation"
```

---

### Task 6: Verify site builds and renders correctly

- [ ] **Step 1: Install Ruby dependencies**

```bash
cd /Users/jiangwengyao/homepage && bundle install
```

Expected: `Bundle complete!` with no errors. If Ruby or Bundler is not installed, run `gem install bundler` first.

- [ ] **Step 2: Start the local development server**

```bash
cd /Users/jiangwengyao/homepage && bundle exec jekyll serve
```

Expected: `Server address: http://127.0.0.1:4000/` — open this in a browser.

- [ ] **Step 3: Visual checklist in browser**

Open http://127.0.0.1:4000 and verify:
- Left sidebar shows: name "Wengyao Jiang", bio "Ph.D. student in CS @ HKU", location "Hong Kong", headshot photo
- Left sidebar shows GitHub and ORCID icons, email link
- Main content shows About Me bio (3 paragraphs)
- Publications section shows the placeholder paper card with badge, title, authors, venue, links
- Education section shows all three entries with correct dates
- No emoji anywhere on the page
- No "Lorem ipsum" text anywhere
- No News / Honors / Talks / Internships sections

---

### Task 7: Create GitHub repository and push

- [ ] **Step 1: Create the repository on GitHub**

Go to https://github.com/new and create a repository named exactly `wenggyaoo.github.io` (must match your GitHub username). Set it to Public.

- [ ] **Step 2: Add remote and push**

```bash
cd /Users/jiangwengyao/homepage && git remote add origin https://github.com/wenggyaoo/wenggyaoo.github.io.git && git branch -M main && git push -u origin main
```

Expected: `Branch 'main' set up to track remote branch 'main' from 'origin'.`

- [ ] **Step 3: Enable GitHub Pages**

In the GitHub repo settings → Pages → Source: select `Deploy from a branch` → Branch: `main` → Folder: `/ (root)` → Save.

- [ ] **Step 4: Verify deployment**

Wait 2-3 minutes, then open https://wenggyaoo.github.io in a browser. The site should be live and match what you saw locally.

---

## Adding Real Publications Later

When you have a paper to add, follow this pattern in `_pages/about.md`:

```markdown
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">ICML 2025</div><img src='images/your-paper-teaser.png' alt="paper name" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

[Your Paper Title](https://arxiv.org/abs/xxxx.xxxxx)

**Wengyao Jiang**, Co-Author 1, Co-Author 2

*International Conference on Machine Learning (ICML), 2025*

[**Paper**](https://arxiv.org/abs/xxxx.xxxxx) \| [**Code**](https://github.com/wenggyaoo/repo)
</div>
</div>
```

Place the teaser image at `images/your-paper-teaser.png` (recommended size: 500x300px).
