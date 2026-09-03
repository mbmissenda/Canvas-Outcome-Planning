# Reading a Mastery Score

A plain-language toolkit for planning, interpreting, and acting on **Canvas Learning Outcomes** data — built for department chairs, program directors, and faculty who do academic assessment.

It exists because of one recurring misreport: a Canvas outcome number, across a cohort, is a **pass rate** — the share of students who cleared the mastery line — **not** the average grade on an assignment. Most of us are trained to read "average" as a mean, so we say the number wrong. This toolkit separates *setting up* a measure from *interpreting* it, and gives you language you can drop straight into a report.

> **New to Canvas Outcomes?** Start with Instructure's official setup guide — [What are Outcomes?](https://community.instructure.com/en/kb/articles/662762-what-are-outcomes) — then come back here for the part their docs don't cover: reading the number correctly.

## What's here

| File | What it is | Who it's for |
|------|-----------|--------------|
| `index.html` | An interactive, self-contained worksheet in three parts — **Plan**, **Interpret**, **Act**. Enter real scores and watch the calculation methods disagree; generate correct reporting language; save a dated version record as PDF. Named `index.html` so it loads at the site's root URL. | Anyone building or reading an outcome |
| `mastery-score-desk-card.pdf` | A one-page printable desk card: the high-jump comparison, two fill-in reporting templates, and a say-this / not-that strip. | The people who won't open a browser |

Nothing is stored anywhere. The worksheet keeps no database and sets no cookies — each PDF you save *is* your record. That's deliberate, so it's safe to host publicly.

## Use it

**Interactive worksheet** — open `index.html` in any browser (or visit the GitHub Pages link below). Work top to bottom:

1. **Plan** — name the outcome, decide where it's measured, choose a calculation method *and record why*, set the mastery line, run the integration check, lock the version, and note where the data lives.
2. **Interpret** — plug a student's scores into the three-method calculator, then enter your cohort counts to see the pass rate for what it is. The reporting sentence writes itself from your entries.
3. **Act** — name the one change the result drives, assign it, set a review date.

Use the **Save as PDF** buttons to keep a dated record. There's no login and no save button beyond that — by design.

**Desk card** — print `mastery-score-desk-card.pdf` double-sided or single, hand it out, keep one by the gradebook.

## Publish it on GitHub Pages

1. Put both files in a repository (a `docs/` folder or the repo root).
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*, pick your branch, and choose the folder (`/root` or `/docs`).
4. Save. Because the worksheet is named `index.html`, it loads at your site's root URL:
   `https://<your-username>.github.io/<repo-name>/`

   (The desk card is then at `https://<your-username>.github.io/<repo-name>/mastery-score-desk-card.pdf`.)

No build step, no dependencies, no framework. It's a single HTML file with fonts loaded from Google Fonts.

## Two honest caveats

Read these before you rely on the numbers in front of an accreditor.

**The decaying-average math.** The worksheet uses the standard model — most recent score weighted 65%, the mean of earlier scores 35%. Canvas has fiddly edge cases in how the first one or two scores are handled, and Instructure has renamed and adjusted this method ("Decaying Average" → "Weighted Average") over time. The *direction* (recency-weighting) is reliable; **confirm the exact corner arithmetic in your own Canvas instance.**

**New Quizzes and the Learning Mastery Gradebook.** Outcomes aligned at the item level in **New Quizzes** have historically **not** populated the Learning Mastery Gradebook. Pull those results from the New Quizzes item/outcomes report, the Outcome Results API (`/api/v1/courses/:id/outcome_results`), or an account-level export instead. This behavior has been a moving target — **verify current behavior in your instance before you present.** The fastest way to be sure: build one New Quiz, align an outcome, take it as a test student, and check where the result appears.

## The idea in one paragraph

Setting an outcome up is a *build* skill. Reading the result is a *statistical* skill, and it's the one nobody teaches. The mastery number counts who crossed a line; it is blind to how far above or below the line anyone landed. That's the right question for competency-based assessment — you usually *do* want "what proportion reached competency." The mistake isn't that Canvas counts crossings; it's reporting the crossing rate as if it were a mean. Name it as a pass rate, pair it with the raw distribution when scores cluster near the bar, and you're both accurate and using the tool for what it's good at.

## License

Released under **CC BY 4.0** — share and adapt freely, with attribution. Fonts (Inter, Newsreader) are used under the SIL Open Font License.
