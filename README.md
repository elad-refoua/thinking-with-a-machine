# Landing page for the QR — GitHub Pages

When a visitor scans the giant QR on the poster, they land here. This page:
- Says who/what the agent is
- Offers three chat options (ChatGPT GPT, Gemini Gem, Claude)
- Carries the demo disclaimer (no data access)
- Links to the full paper PDF

## Files

| File | Purpose |
|------|---------|
| `index.html` | The landing page. Self-contained — no JS, no external CDN, inline CSS. |
| `agent.jpg` | A square Nano Banana–generated portrait of the demo agent. Add this file before deploying (see below). |

## Before deploying — search-and-replace four placeholders in `index.html`

| Placeholder | What to put there |
|-------------|------|
| `CHATGPT_BOT_URL_HERE` | The public share URL of your ChatGPT GPT. From the GPT builder → "Share" → "Anyone with the link." |
| `GEMINI_BOT_URL_HERE` | The Gemini Gem share URL. From gemini.google.com/gems → Share → Public link. |
| `CLAUDE_BOT_URL_HERE` | The Claude Project share URL, if you set one up. If you skip Claude, set `href="#"` and add `aria-disabled="true"` to that `<a>` tag, or just delete the block. |
| `PAPER_DOWNLOAD_URL_HERE` | Stable public link to the camera-ready PDF. Easiest options: Dropbox public share, Google Drive "anyone with the link," GitHub raw file URL, OSF preprint, or the ACL Anthology link once the proceedings publish. |

## Generating the agent portrait

The page shows a circular portrait of "the agent." Generate one with Gemini / Nano Banana:

**Prompt for Gemini / Nano Banana / ChatGPT image generation:**

> A serene, slightly abstract portrait of an AI research collaborator: a softly geometric figure with warm muted-blue and parchment tones, hints of academic books and code symbols around the shoulders, intelligent eyes, no readable text, no logos. Square framing, soft natural light, professional illustration style suitable for an academic conference poster landing page. The figure should feel thoughtful and trustworthy, not menacing or hyper-realistic.

Save the output as `agent.jpg` (square, ≥600×600 px) in this folder. If `agent.jpg` is missing, the page hides the image area gracefully — the rest of the layout still works.

## Deploying to GitHub Pages

1. Create a new GitHub repo (e.g., `thinking-with-a-machine-poster`).
2. Copy these two files (`index.html` + `agent.jpg`) into the repo root.
3. Push.
4. Settings → Pages → Source: `main`, folder: `/ (root)` → Save.
5. GitHub Pages will publish at `https://YOUR-GITHUB-USER.github.io/thinking-with-a-machine-poster/`.
6. Use that URL when you run `generate_qr.py` for the poster.

**Custom domain (optional):** Settings → Pages → Custom domain. Most conference visitors don't care, but a short URL (e.g., `tinyurl.com/twam-agent`) on a poster scans more reliably from far away — consider running the final GitHub URL through a URL shortener once and encoding *that* in the QR.

## Local preview

Open `index.html` in any browser locally — it renders without a server. To test the mobile experience, open Chrome DevTools → Toggle device toolbar → iPhone 14 Pro.
