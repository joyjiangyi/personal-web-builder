# personal-web-builder

A Claude Code skill that guides anyone through building a website from scratch — personal portfolio, brand site, product landing page, or event page.

**Every website comes out different.** The skill starts by deeply understanding what you want to put on the site and who it's for, then designs the structure and style around your content — not the other way around.

**Full flow: deep requirements chat → content checklist → blueprint → build → AI video prompts → local preview.**

---

## Install

```bash
git clone https://github.com/joyjiangyi/personal-web-builder.git ~/.claude/skills/personal-web-builder
```

That's it. No path setup. No config files.

---

## Usage

Just tell Claude what you want to build:

> "帮我做个人网站" / "做个品牌官网" / "搭个产品落地页"
> "build my portfolio / brand site / landing page"

Claude will:

1. **Have a real conversation** — ask what content you want, who it's for, what format each piece is (video link? image? text?)
2. **Confirm a content checklist** — before designing anything
3. **Output a custom blueprint** — page structure, copy drafts, and a visual style derived from *your* content
4. **Build the website** — single-file HTML, styled uniquely for you
5. **Give you AI video prompts** — matched to your style (if you want a video background)
6. **Walk you through local preview** — `npx serve` + checklist

**Output:**
```
your-project/
├── index.html          ← full website, all CSS/JS inline
└── assets/
    ├── video/          ← background video (yours to provide)
    └── img/            ← your photos and images
```

---

## What you get

- A website designed around **your** content — not a template
- Structure and style derived from what you actually want to show
- Scroll-scrubbing video background (optional, GSAP ScrollTrigger)
- Typography and color matched to your brand/personality
- Mobile-responsive layout
- Works for all site types:

| Site type | Examples |
|-----------|----------|
| Personal portfolio | Designer, filmmaker, developer, marketer |
| Brand / company site | Studio, agency, small business |
| Product landing page | App, SaaS, physical product |
| Event / campaign page | Launch, festival, conference |

---

## Local preview

```bash
# Must use npx serve — don't double-click the HTML file
npx serve .
# Open http://localhost:3000
```

---

## Replace the default video

The skill uses a dark cinematic placeholder. To swap in your own video:

```bash
# Step 1: Re-encode your video for scrubbing (required)
ffmpeg -i your-video.mp4 -movflags +faststart -c copy output.mp4

# Step 2: Drop it into assets/video/
# Step 3: Update the <source> path in index.html
```

---

## Deployment (Part 2)

Local version only for now. GitHub Pages + custom domain deployment guide coming in Part 2.

---

## Inspiration

Born from a real 9-day build process — 7 Claude Code sessions, every decision logged.
