# Subnet

Short, gamified practice rounds for the **AWS Certified Solutions Architect – Associate (SAA-C03)** exam. Built to be used on a phone, in ten minutes, standing in line somewhere.

**Live:** https://vinadomi.github.io/subnet/

---

## What it does

- **10 questions a round**, roughly 10–15 minutes including the explanations.
- **Rounds match the published exam blueprint.** Domain 1 Secure 30%, Domain 2 Resilient 26%, Domain 3 High-Performing 24%, Domain 4 Cost-Optimized 20% — the tenth question is drawn probabilistically so the ratio holds across rounds rather than within any single one.
- **Both real response types**: multiple choice with three distractors, and multiple response with five options and "Choose 2."
- **75 scenario questions**, each with an explanation covering why the correct answer wins *and* why the tempting distractor loses.
- **XP, levels, streak bonuses, mastery bars per domain, and 10 badges.** A Weak Spots mode unlocks after four misses and re-serves questions you've gotten wrong more often than right.
- **Missed questions collect into a review list** at the end of each round.
- Works offline once loaded. Progress saves to `localStorage` on the device.

## Question bank

All 75 items are original, written against the [public SAA-C03 exam guide](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.html). No real exam content is reproduced here — that material is confidential, and memorizing it wouldn't teach you anything anyway.

Questions live in the `QUESTIONS` array near the top of the `<script>` block in `index.html`:

```js
{
  id: 76,
  d: 3,                        // domain 1-4
  tag: "CloudFront",           // shown as a chip above the question
  q: "Scenario text...",
  o: ["option A", "option B", "option C", "option D"],
  a: [0],                      // indices of correct options; 2+ makes it multi-response
  e: "Why this is right, and why the close call is wrong."
}
```

Option order is shuffled at render time, so never write an explanation that refers to "option B."

## Running locally

It's one file with no build step. Open `index.html` in a browser, or serve it if you want the service worker active:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying

Push to `main` and enable Pages (Settings → Pages → Source: Deploy from a branch → `main` / root).

After editing `index.html`, **bump `CACHE` in `sw.js`** (`subnet-v1` → `subnet-v2`). Otherwise phones that already installed the app keep serving the cached copy and your changes appear not to have shipped.

## Install on a phone

- **iOS:** open in Safari → Share → Add to Home Screen.
- **Android:** open in Chrome → menu → Install app.

Launches full-screen with no browser chrome, and works with no signal.

## License

MIT. See `LICENSE`.
