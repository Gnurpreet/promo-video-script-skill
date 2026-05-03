---
name: promo-video-script
description: "Generate a complete animated product promo video script from a website URL. Use this skill whenever a user wants to create a product video, promo script, animated explainer, marketing video, or sales video for a product or service. Triggers on phrases like \"promo video\", \"product video script\", \"marketing video\", \"explainer video\", \"video for my product/website/app\", or any request to turn a product or website into a video script. Walk the user through a guided multi-step process: fetch the site, extract features, let user choose features and benefits, then produce a full scene-by-scene animated script with visual direction matched to the brand's aesthetic."
---

# Promo Video Script Skill

Generate a polished 7–10 scene animated product promo video script through a guided, conversational process. Each step narrows the focus so the final script is specific, benefit-driven, and visually faithful to the product's brand. This script should be ready input for Claude Design animation creator. It should contain everything that Claude Design will need to create the promo video

---

## Step-by-step workflow

### Step 1 — Get the website URL

Ask the user for their product's website URL if they haven't already provided one.
Confirm you'll fetch it and extract key information.

---

### Step 2 — Fetch and analyse the website

Use `web_fetch` on the URL. Extract and internally note:

**Product information**
- Product / company name
- One-line description of what it does
- Target audience (inferred from copy and imagery descriptions)
- Tone of voice (e.g. playful, enterprise, minimal, bold)

**Visual / brand style** — describe concretely:
- Primary and secondary colour palette (hex or descriptive)
- Typography style (serif/sans-serif, weight, mood)
- Layout rhythm (spacious/dense, card-based, full-bleed)
- Motion cues visible in copy ("instant", "smooth", "powerful", animations mentioned)
- Photography or illustration style if inferable from alt text or copy
- Overall aesthetic keyword (e.g. "clean SaaS", "bold consumer", "warm startup", "dark-mode tech")

**Features** — identify at least 6–8 distinct product features or capabilities from
the site copy, headlines, feature grids, or pricing tables. Rank by how prominently
they're featured on the page.

---

### Step 3 — Present findings and offer top 5 features for selection

Show the user a brief summary (3–5 sentences) of what the product is and who it's for.

Then present **exactly 5 features** as a numbered list. For each feature write:
- A short feature name (3–6 words)
- One sentence explaining the user benefit (not just what it does, but why it matters)

Ask the user to **choose 2 or 3 features** they want the video to focus on.
Use `ask_user_input_v0` if available, otherwise ask in plain text.

Example format:
```
Here are 5 standout features I found. Pick 2 or 3 to focus the video on:

1. **One-click export** — Save your work as a polished file in seconds, no manual steps.
2. **Real-time collaboration** — Multiple teammates edit together live, no merge conflicts.
3. **AI-powered suggestions** — Get smart prompts as you work, cutting creation time in half.
4. **Brand kit integration** — Pull in your colours and fonts automatically, every time.
5. **Version history** — Roll back to any saved state, so nothing is ever lost.
```

---

### Step 4 — Generate business benefits for each chosen feature

For each feature the user selected, come up with **3 concrete business benefits**.
Benefits must be outcome-oriented: revenue, time saved, risk reduced, team velocity,
customer satisfaction, competitive edge. Avoid generic filler.

Present them clearly grouped by feature. Ask the user to **select 1–2 benefits per
feature** that resonate most. These become the script's core messages.

Example format:
```
Great choices. For each feature, here are the business benefits — pick 1 or 2 per feature:

**One-click export**
  A. Cuts delivery time by up to 60%, letting teams ship faster.
  B. Eliminates formatting errors that cause rework and client revisions.
  C. Frees designers from repetitive tasks so they focus on creative work.

**Real-time collaboration**
  A. Reduces back-and-forth emails, saving hours per project.
  B. Keeps remote teams aligned without extra meetings.
  C. Shortens approval cycles, getting work signed off faster.
```

---

### Step 5 — Confirm the script brief

Before writing, confirm back to the user in 3–5 bullet points:
- Product name and audience
- Chosen features (with their selected benefits)
- Visual style (from your brand analysis)
- Tone (serious/playful/inspirational etc.)
- Implied call to action from the site (free trial, book a demo, sign up, etc.)

Ask: "Does this look right before I write the full script?"

---

### Step 6 — Write the full animated promo video script

Produce a **7–10 scene script**. Structure each scene with these labelled fields:

```
SCENE [N] — [Scene title in caps]
Duration: [e.g. 4–6 sec]
Visual: [Detailed description of what's on screen — layout, motion, colours, elements]
Animation: [Specific motion direction — entrance, exit, transition, timing feel]
Text: [On-screen text, clearly labelled]
```

#### Mandatory scene structure

| Scene | Purpose |
|-------|---------|
| 1 | **Hook** — Grab attention. Problem statement or bold visual opener. No product yet. |
| 2 | **Problem** — Amplify the pain point the audience recognises. |
| 3 | **Product introduction** — First reveal of the product name and category. |
| 4–6 | **Feature + benefit scenes** — One scene per chosen feature. Show the feature, state the benefit. |
| 7 | **Social proof / credibility** — Customer quote, logo wall, stat, or trust signal (use placeholder if none found on site). |
| 8–9 | **Vision / transformation** — Show life after using the product. Emotional resolution. |
| 10 | **CTA** — Clear call to action matching the site's primary CTA. Brand close. |

Adjust scene count (7–10) based on how many features were chosen (2 features → 7–8 scenes; 3 features → 9–10 scenes).


#### Visual direction rules

- **Every scene's Visual field must reference the brand palette and style** identified in Step 2.
- Instruct the model to download the logo & other brand assets from the site and use them in the video where relevant.
- Instruct the model to download any relevant imagery or icons from the site or the Internet to use in the video.
- Describe motion precisely: "card slides in from left at 0.3s with ease-out", not "element appears".
- Include text treatment: font weight, size relationship, colour usage. The main text of each scene should be centered and prominant. Treat this as a animated headline to grab the viewer's attention.
- Reference the brand aesthetic keyword consistently (e.g. "clean SaaS minimal layout", "dark-mode tech with neon accent").
- Specify the scene transition for each scene. Transitions should not be disconnected. Some visual element should lead to the transition to next scene (like continueing lines, icons jumps, zoom-in, zoom outs etc.)
- Use popular UX element preferably from the website like - cards, buttons, forms, charts, dashboards etc. But, keep the UI simple to avoid overwhelming the viewer. The focus should be on the feature and its benefit, not on detailed UI.
- Assume the video is produced in a motion design tool (After Effects, Rive, CSS animation, or similar) — write for an animator, not a live-action director.

#### Tone and copy rules

- On-screen text: max 6 words. Punchy, benefit-first
- No jargon unless the brand uses it deliberately.
- Active voice throughout.
- Final CTA must match the exact wording on the site where possible.

---

### Step 7 — Deliver the script

Output the complete script in clean Markdown, scene by scene. This MD file will be copy-pasted to Claude design for creating the video, so it should be instructional to Claude Design or similar tools.

After the script, append:

**Production notes** (brief):
- Suggested total video length
- Recommended aspect ratio (16:9, 9:16, 1:1) based on the product's likely distribution channel (inferred from site)
- One sentence on animation style recommendation (e.g. "Kinetic type with smooth morphing transitions suits this brand's clean SaaS aesthetic")

---

## Quality checklist (self-review before delivering)

Before outputting the final script, verify:
- [ ] Every scene has all 6 fields (Scene title, Duration, Visual, Animation, Text, Transition)
- [ ] Brand colours and style referenced in at least 60% of Visual fields
- [ ] Each chosen feature appears in exactly one dedicated scene
- [ ] Each selected benefit is stated explicitly (on-screen text)
- [ ] Scene 1 does NOT mention the product by name
- [ ] CTA in final scene matches the site's primary CTA
- [ ] Total scenes are between 7 and 10
- [ ] On-screen text ≤6 words and is nice and bold
- [ ] Every scene has a visual transition to the next scene
- [ ] Production notes included at the end
- [ ] Production notes mention headline to be kept big bold with animation. 
---

## Handling edge cases

**Site is behind a login / blocks fetch**: Ask the user to paste the homepage copy or describe the product. Proceed with what they provide.

**Product has too many features**: Still limit to 5 presented options. Choose the most prominently featured ones on the homepage or pricing page.

**No clear CTA on the site**: Default to "Try it free" or ask the user for their preferred CTA.

**B2B vs B2C distinction**: If the product is clearly enterprise (pricing tiers, "book a demo", "contact sales"), lean benefits toward ROI, time savings, and risk reduction. If consumer, lean toward ease, delight, and transformation.

**No visual style cues on the page**: Use the product category to infer a sensible default (e.g. fintech → dark, trustworthy; wellness app → warm, soft gradients; dev tool → minimal, monospace accents).