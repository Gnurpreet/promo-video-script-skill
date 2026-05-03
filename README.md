# promo-video-script-skill

A Claude skill that turns any product website into a polished, scene-by-scene animated promo video script — through a guided, conversational process.

---

## What it does

Give Claude a URL. The skill fetches the site, extracts the brand style and key features, walks you through choosing what to highlight, and produces a **7–10 scene animated video script** ready to hand off to a motion designer or drop into Claude's design tools.

Each scene comes with:
- Duration
- Visual direction (colours, layout, motion)
- Animation instructions (entrance, exit, timing)
- On-screen text (≤6 words, punchy)
- Transition to the next scene

The output is a Markdown file — clean enough to paste directly into After Effects briefs, Rive, or Claude Design.

---

## How to install

1. Go to **Claude.ai → Settings → Skills**
2. Click **Add skill**
3. Paste the raw URL of `SKILL.md` from this repo:
   ```
   https://raw.githubusercontent.com/YOUR_USERNAME/promo-video-script-skill/main/SKILL.md
   ```
4. Save. Claude will now recognise promo video requests and use this skill automatically.

> Skills require a Claude Pro or Team plan.

---

## How to use

Just describe what you want in natural language. Any of these will trigger the skill:

- *"Make a promo video for my app — here's the URL: …"*
- *"I need a product video script for spurline.in"*
- *"Create a 60-second animated explainer for this SaaS tool"*
- *"Write a marketing video script from my website"*

Claude will then guide you step by step:

| Step | What happens |
|------|-------------|
| 1 | Asks for (or confirms) your website URL |
| 2 | Fetches the site, extracts brand style + features |
| 3 | Presents 5 features — you pick 2 or 3 to focus on |
| 4 | Shows business benefits for each — you pick 1 or 2 per feature |
| 5 | Confirms the script brief before writing |
| 6 | Writes the full 7–10 scene animated script |
| 7 | Delivers it as clean Markdown with production notes |

Once the script is generated

 - Review it & vibe with your AI of choice to customize it
 - Copy paste the script into [Claude Design](claude.ai/design) > From Template > Animation and let it cook
 - After Claude design is done, use [ClaudeVideoExport.com](claudevideoexport.com) to get an MP4
 - Now, you can post the video to your website, Youtube, Instagram or anywhere you like
 
---

## Sample output structure

```
SCENE 1 — HOOK
Duration: 4–5 sec
Visual: Dark canvas. A single overflowing inbox animates in — emails stack up fast, counter ticking. Brand accent colour (#FF4D00) pulses on the counter. Clean sans-serif layout.
Animation: Emails cascade from top at 0.2s intervals, ease-in. Counter spins. Screen shakes subtly at peak.
Text: DROWNING IN ORDERS?
Transition: Counter explodes into particles → reforms as the product logo in Scene 2.

SCENE 2 — PROBLEM
...
```

---

## Production notes included

Every script ends with:
- Suggested total video length
- Recommended aspect ratio (16:9 / 9:16 / 1:1)
- Animation style recommendation

---

## Edge cases handled

- Site behind login → asks you to paste the copy
- Too many features → limits to 5 best options
- No CTA on site → defaults to "Try it free" or asks you
- No visual style cues → infers from product category (fintech, wellness, dev tool, etc.)

---

## License

MIT — see [LICENSE](LICENSE)

---

## Author

Built by [Gurpreet Singh](https://spurline.in) / Spurline Internet Services LLP
