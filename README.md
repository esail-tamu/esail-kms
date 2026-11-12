# ESAIL KMS

Training and tutorials for ESAIL, built with [MkDocs](https://www.mkdocs.org/) + [Material](https://squidfunk.github.io/mkdocs-material/) and published to GitHub Pages.

## Local development

```
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m mkdocs serve
```

Then open http://127.0.0.1:8000.

## Adding a new training

1. Create a folder under `docs/trainings/<your-training>/` with an `index.md`.
2. Add it to the `nav` section of `mkdocs.yml`.
3. Add a card linking to it on `docs/index.md` and a row in `docs/trainings/index.md`.
4. Give the page tags in its front matter so it shows up on the [tags index](docs/tags.md):
   ```
   ---
   tags:
     - beginner
   ---
   ```
   Tags must be in the `tags_allowed` list in `mkdocs.yml` — add new ones there as the vocabulary grows, so tags stay a controlled, browsable set instead of sprawling. If the training belongs to the GAP student program, tag it `gap-bronze`, `gap-silver`, or `gap-gold` for the level it's part of.
5. Push to `main` — the GitHub Action builds and deploys automatically.

See **[AUTHORING.md](AUTHORING.md)** for the deeper patterns — the self-grading quiz format, Formspree integration, and a couple of non-obvious dark-mode/JS bugs worth knowing about before you build the next one.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which runs `mkdocs gh-deploy` to publish the built site to the `gh-pages` branch. GitHub Pages must be configured (Settings → Pages) to serve from the `gh-pages` branch.
