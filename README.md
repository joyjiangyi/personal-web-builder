# personal-web-builder

A Claude Code skill that guides anyone through building a website from scratch — personal portfolio, brand site, product landing page, or event page.

**Every website comes out different.** The skill starts by deeply understanding what you want to put on the site and who it's for, then designs the structure and style around your content — not the other way around.

**Full flow: deep requirements chat → content checklist → blueprint → build → AI video prompts → local preview.**

---

## Install

**Prerequisites: Claude Code**

```bash
# Install Claude Code if you haven't
npm install -g @anthropic-ai/claude-code

# Install this skill
git clone https://github.com/joyjiangyi/personal-web-builder.git ~/.claude/skills/personal-web-builder
```

No path setup. No config files.

---

## Usage

Open Claude Code in any folder, then just say:

> "帮我做个人网站" / "做个品牌官网" / "搭个产品落地页"
> "build my portfolio / brand site / landing page"

Claude will guide you through the full flow automatically.

---

## Full Workflow

### Phase 1 — Chat about your needs
Claude asks what you want on the site, who it's for, and what format each piece of content is (local video file? YouTube link? images? text?). One question at a time.

### Phase 2 — Confirm content checklist
Claude outputs a structured list of all your content modules. You confirm before anything gets designed.

### Phase 3 — Approve the blueprint
Claude proposes a page structure, copy drafts, color palette, and typography — all derived from your content. You approve before any code is written.

### Phase 4 — Build
Claude builds a single-file `index.html` with all CSS/JS inline. After each section, Claude takes a screenshot for you to review before continuing.

**Output structure:**
```
your-project/
├── index.html          ← full website, all CSS/JS inline
└── assets/
    ├── video/          ← your background video goes here
    └── img/            ← your photos and images
```

### Phase 5 — AI video background (optional)

If you want a cinematic scroll-scrubbing video background, Claude gives you a ready-to-use AI prompt matched to your site's style. Here's how to use it:

**Step 1 — Generate your video**

Copy the prompt Claude gives you into one of these tools:
- [Kling](https://klingai.com) — recommended, best quality
- [Runway Gen-3](https://runwayml.com)
- [Pika](https://pika.art)

Generate a 10–30 second clip. Download the file.

**Step 2 — Re-encode the video (required)**

The video must be re-encoded for scroll-scrubbing to work. Run this in your terminal:

```bash
# If your file is .mp4
ffmpeg -i your-video.mp4 -movflags +faststart -c copy assets/video/bg.mp4

# If your file is .mov
ffmpeg -i your-video.mov -c:v libx264 -crf 22 -movflags +faststart -pix_fmt yuv420p assets/video/bg.mp4
```

> Don't have ffmpeg? Install it: `brew install ffmpeg` (Mac) or [ffmpeg.org](https://ffmpeg.org/download.html)

**Step 3 — Tell Claude the filename**

Just say: `"视频文件名是 bg.mp4，帮我替换进去"` — Claude updates the HTML path for you.

**Step 4 — Verify it works**

```bash
npx serve .
# Open http://localhost:3000
# Scroll the page — the video should scrub with your scroll position
```

> ⚠️ Always use `npx serve` to preview. Don't double-click the HTML file — video scrubbing won't work via `file://` protocol.

### Phase 6 — Local preview checklist

Before calling it done, verify:
- [ ] Loading screen fades out smoothly
- [ ] Video scrubs with scroll (no stuttering, no frame-tearing)
- [ ] All sections display correctly, no blank areas
- [ ] Mobile layout works (Chrome DevTools → 375px width)
- [ ] All links and buttons work correctly

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

## Deployment (Part 2)

Local version only for now. GitHub Pages + custom domain deployment guide coming in Part 2.

---

## Inspiration

Born from a real 9-day build process — 7 Claude Code sessions, every decision logged.
