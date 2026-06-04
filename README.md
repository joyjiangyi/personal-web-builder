# personal-web-builder

A Claude Code skill that guides anyone through building a cinematic personal website from scratch — portfolio, job search, or personal brand.

**Full flow: interview → blueprint → build → AI video prompts → local preview.**

---

## Install

```bash
git clone https://github.com/joyjiangyi/personal-web-builder.git ~/.claude/skills/personal-web-builder
```

That's it. No path setup. No config files.

---

## Usage

Just tell Claude you want a personal website:

> "帮我做个人网站"
> "搭一个作品集"
> "build my personal portfolio"

Claude will:

1. **Ask 5 questions** — name, purpose, audience, style, color preference (one at a time)
2. **Output a blueprint** — page structure + copy drafts, tailored to your profession
3. **Build the website** — single-file HTML with cinematic scroll-scrubbing video background
4. **Give you AI video prompts** — 3 options: AI-generated (Runway/Kling/Pika), Pexels free stock, or keep the default
5. **Walk you through local preview** — `npx serve` + 5-item checklist

**Output:**
```
your-project/
├── index.html          ← full website, all CSS/JS inline
└── assets/
    ├── video/          ← background video (default: Grand Budapest curtain)
    └── img/            ← your photos and images
```

---

## What you get

- Cinematic scroll-scrubbing video background (GSAP ScrollTrigger)
- Smooth scroll snap between sections
- Dark theme with warm gold accents (`#0f0e0d` bg · `#c9a84c` gold · `#f0e8d8` cream)
- Cormorant Garamond + Inter typography
- Mobile-responsive layout
- Smart page recommendations based on your profession:

| Profession | Extra modules |
|-----------|--------------|
| Film / Creative | Horizontal scroll poster reel |
| Developer / PM | Products & open-source projects |
| Marketing / Ops | Campaign results & data highlights |
| Designer | Visual portfolio (large image grid) |
| Content creator | Channel stats & content showcase |

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
