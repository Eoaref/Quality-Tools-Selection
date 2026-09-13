# Quality Tools: Worked Example + Practice Quiz

Two self-contained pages, no build step, no dependencies to install (both load Chart.js from a CDN):

- **`worked-example.html`** — one dataset (Harlow Components, Line 3), four tabs (Pareto / Control Chart / Histogram / Scatter). Each tab states a question, shows the matching chart, and explains why the other three tools fall short of answering it. Meant to be read before the quiz.
- **`index.html`** — the practice quiz, four rounds across two scripted scenarios. Students are given a dataset and a question — with a named person asking and a concrete stake — pick from the same four tools, and get the chart plus feedback. Wrong picks render *that* chart too, with a short explanation of why it doesn't answer the question, and the round stays open until they pick correctly.

The two pages link to each other (top-left of each).

### The two scenarios in the quiz

**Harlow Components — Line 3** (injection molding, rounds 1–2). You're covering QC for three weeks; your supervisor Dana hands you 20 days of logs (barrel temperature, six defect types, sampled part weight).
- Round 1: Dana needs one defect prioritized for Friday's corrective-action meeting → **Pareto Chart**.
- Round 2: an operator says the line "feels off"; Dana wants proof it's a real shift, not noise, before pulling anyone off the floor → **Control Chart**.

**Millbrook Bakery — Line 7** (bakery packaging, rounds 3–4). The oven was recently refurbished and is being watched closely; same 20-day log structure re-themed (oven temperature, six defect types, sampled loaf weight).
- Round 3: a retail buyer's contract requires loaves to average 500 g; is the line on target and what's the normal spread? → **Histogram**.
- Round 4: maintenance logs suggest the oven runs hot; does that line up with more defects, before filing a warranty claim? → **Scatter Diagram**.

## Deploy it on GitHub Pages (free, ~2 minutes)

1. Create a new repository on GitHub (public, so Pages can serve it on the free tier).
2. Add `index.html`, `worked-example.html`, and this `README.md` to the repo root (drag-and-drop on github.com works fine, or:
   ```
   git init
   git add index.html worked-example.html README.md
   git commit -m "Add quality tools worked example and quiz"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch", **Branch** to `main` and folder to `/ (root)`, then **Save**.
5. GitHub gives you a URL like `https://<your-username>.github.io/<repo-name>/` within a minute or two — that's the quiz link to share with students. The worked example is at the same URL plus `worked-example.html`.

## Editing the content

**`index.html`** (quiz) — everything lives in its `<script>` block:
- `datasetA` / `datasetB` — the two 20-day production datasets each round draws from.
- `rounds` — one entry per challenge: which dataset, the question (`issue`), which tool is `correct`, and an `explanations` object with feedback text for all four tools (correct and incorrect).

To add a round, add another dataset and another object to `rounds` — the tool buttons, chart rendering, and progress dots all work off that array automatically.

**`worked-example.html`** — its `<script>` block has one `dataset` and a `TOOLS` array with `question` / `why` / `what` / `not` text per tool. Edit those strings, or swap in a different `dataset` object (same shape: `day`, `temp`, six defect-type counts, `weight`), to retheme it.

## License

This tool was created as an aid to help students recognize the role, value, and application of some common quality tools. This interactive example was planned and structured by the instructor; the code was created by Claude (Anthropic) and deployed by the instructor. It is for educational purposes only — names and entities are fictional, used solely to give context to the problems.

Comments, questions, or spotted errors: earef@outlook.com

Licensed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/) — share the original only, no modifications, no commercial use.
