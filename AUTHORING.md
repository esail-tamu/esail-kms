# Authoring Guide

Internal notes for whoever (human or agent) adds the next training to this site. `README.md` has the quick checklist; this file explains the *why* behind the patterns, including a few non-obvious bugs that are easy to reintroduce if you don't know to look for them.

## Page types

Each training lives under `docs/trainings/<slug>/` and is built from up to three pages:

- **`index.md`** — the actual training content. Required.
- **`quiz.md`** — an optional self-graded check. See "The quiz pattern" below.
- **`thank-you.md`** — only needed if the quiz submits somewhere; a plain landing page the quiz redirects to a few seconds after a successful submission. Not listed in `nav` (it's a redirect target, not something people browse to) — MkDocs still builds it, just logs an informational "not included in nav" note, which is expected and fine.

## Listing a new training

1. Folder + `index.md` under `docs/trainings/<slug>/`.
2. Add it to the `nav:` block in `mkdocs.yml`.
3. Add a card to the grid on `docs/index.md` (the KMS home page).
4. Add a row to `docs/trainings/index.md`.
5. Give the page `tags:` front matter — every tag must already be in `tags_allowed` in `mkdocs.yml`, or the build fails. Add new tags there deliberately; it's an allow-list specifically so tags stay a curated, browsable set instead of sprawling.
6. If the training is part of the GAP student program, tag it with the level it belongs to: `gap-bronze`, `gap-silver`, or `gap-gold` (GAP-bronze is the track for new students — this File Naming Convention training is part of it).
7. Build locally (`mkdocs build --strict`) and actually look at it in a browser before pushing — a clean build does not mean the page looks or works right, especially for anything with custom JS (see below).

## "Last updated" dates

Every page footer shows a "Last updated" date (via `mkdocs-git-revision-date-localized-plugin`), and that date is a link to the file's real commit history on GitHub (`overrides/partials/source-file.html` adds the link; the plugin itself only renders text). This depends on the full git log being available, which means **the GitHub Action's checkout must use `fetch-depth: 0`** — the default shallow clone only has the latest commit, and the plugin would silently show the wrong (or same) date for every file. If you ever touch `.github/workflows/deploy.yml`, don't let that setting get lost.

## The quiz pattern

The File Naming Convention quiz (`quiz.md`) is a reusable pattern, not a one-off:

- **Mastery loop, not score-and-reveal.** One question at a time; a wrong pick gets struck through and disabled (forcing real elimination, not guessing), and the question doesn't advance until the right answer is chosen. On correct, it shows "Correct!" *and waits* for the learner to click "Next question" (or "See results" on the last one) rather than auto-advancing — people need a moment to actually read the right answer, not just note they got it. Finishing the quiz already means "got everything right," so there's nothing left to grade.
- **Question bank with randomization**, not a fixed list. Each of the 10 "slots" holds 2+ phrasing variants (different example values, not just reworded) — one is picked at random per session, and its answer options are shuffled too. This is what keeps two learners from seeing an identical quiz, which matters for an ungraded self-check that's easy to share answers for otherwise. When writing distractors: make them wrong for a *structural* reason (wrong field order, wrong delimiter, missing a required field), not just "doesn't match the specific numbers given in the prompt" — the latter tests attention to the question, not understanding of the rule.
- **No backend.** Submission goes to Formspree via `fetch(..., {headers: {Accept: "application/json"}})`, which is Formspree's documented AJAX pattern — no external JS library needed, just a plain `<form>` whose `action` points at the Formspree endpoint. A field literally named `email` is what Formspree uses as the Reply-To on the notification it sends. Formspree enforces an "Allowed Domain" per **project** (not per-form) — set under the project's Settings tab, not the individual form's. A new quiz either reuses an existing Formspree form/project or needs its own; either way, local testing from `127.0.0.1` will always get flagged by Formspree's domain check (expected, not a bug) and needs manual "not spam" approval in the dashboard once.
- **Formspree's native autoresponse-to-submitter feature requires a paid plan** (Professional/Business) — the free tier can't acknowledge the learner's own email automatically. If a training needs that, either upgrade the Formspree plan, or add a second free service (e.g. EmailJS) purely for the participant-facing confirmation, sent via client-side JS alongside the Formspree submission.

### The `document$` / `DOMContentLoaded` gotcha

This theme has `navigation.instant` enabled (SPA-style page swaps). Material exposes `document$`, an observable that fires on every page view including the first — the documented way to run custom per-page JS so it keeps working after an instant-navigation swap, not just on a hard reload.

**The trap:** an inline `<script>` tag runs synchronously at its position in the HTML, which is *before* Material's own bundle (loaded near the end of `<body>`) has executed and defined `document$`. Call `document$.subscribe(...)` directly in an inline script and it works fine when a user clicks into the page from elsewhere on the site (document$ already exists by then) — but throws `ReferenceError: document$ is not defined` and silently does nothing on a true fresh full-page load or reload. This is exactly the kind of bug that passes a casual test (click a nav link, looks fine) and fails in a way that's invisible unless you specifically test a hard reload.

The fix, already applied in `quiz.md`, is to defer to `DOMContentLoaded`, which only fires after the page is parsed and all non-async scripts (including Material's bundle) have run:

```js
window.addEventListener("DOMContentLoaded", function () {
  document$.subscribe(function () {
    // page logic — guard with a dataset flag so it doesn't rebind on every swap
  });
});
```

**Always test both paths**: open the page via a direct URL (fresh load) *and* by clicking into it from another page (instant-nav), not just one or the other.

## Theming

The maroon palette lives in `docs/stylesheets/extra.css`, hooked into Material's custom-color mechanism (`primary: custom` / `accent: custom` in `mkdocs.yml`, since maroon isn't one of Material's built-in palette names). A few hard-won, non-obvious fixes are recorded there in comments — don't remove them without re-testing dark mode:

- `--md-primary-fg-color` (our maroon, `#500000`) is fine as a *background* (the header bar, filled buttons) in both themes, but unreadable as *text* against the dark "slate" scheme's near-black background (contrast ≈1:1). Material uses this token for body links (`--md-typeset-a-color` falls back to it) and for outline-style `.md-button`s' text/border — both needed a dark-mode-only override to a lighter rose (`#d47070`), via `[data-md-color-scheme=slate]` selectors.
- Any new UI element that uses `--md-primary-fg-color` (or a custom color) as **text on a dark/transparent background** needs the same check: screenshot it in dark mode specifically, don't assume the light-mode look carries over. Using it as a **background with light text** (the header, filled buttons) is safe in both themes without extra work.
- Test by forcing dark mode via the browser (toggle the switch, or `document.body.setAttribute('data-md-color-scheme', 'slate')` in the console for a quick check) and actually looking at a screenshot — this class of bug is invisible in the accessibility tree/DOM snapshot, only visible pixels show it.

## Before shipping

1. `mkdocs build --strict` — catches broken links/config, not visual or JS bugs.
2. `mkdocs serve` and open the page locally — test a fresh load *and* an instant-nav click-through for anything with custom JS.
3. For a quiz: actually answer it through once (including a deliberate wrong answer, to see the elimination state), and check both light and dark mode.
4. Clean up generated build output (`site/`) before committing — it's gitignored, but confirm nothing slipped in.
5. Commit, push to `main`, and confirm the GitHub Action (`Deploy MkDocs site`) succeeds before considering it done — a clean local build doesn't guarantee the production deploy step (which runs `mkdocs gh-deploy`) also succeeds.
