# Handoff: ICWSM GitHub/Overleaf project

Repo: https://github.com/ceshwar/icwsm-retrospective
Branch: `main` (default branch)

## Current status

The repository is now structurally complete for Overleaf:

- `.gitignore` is present and excludes LaTeX build artifacts and root compiled PDFs.
- `main.tex` is the only root `.tex` file containing `\documentclass`.
- All manuscript section/table `.tex` files live under `sections/`.
- `aaai2026.sty` is in the repository root.
- The five required figure files are under `figures/` with the exact paths referenced by the manuscript.
- `sections/references.tex` is input directly by `main.tex`, so the build does not depend on committing a generated `.bbl`.
- The ICWSM checklist is after the references and before the appendices.
- Release language says the corpus, derived measurements, analysis code, and documentation will be released upon publication.

A local build of the same manuscript source completed successfully with `pdflatex` twice. It produced an 18-page PDF including checklist and appendices, with no undefined references/citations or LaTeX errors. The main paper and references fit within the 11-page limit; the checklist follows them.

## One thing worth replacing if convenient

The GitHub connector required aggressive downsampling for two binary figure uploads. The repo versions compile, but for submission-quality rendering replace these with the latest fixed high-resolution versions from `icwsm20_fixed_figures.zip` / the current Overleaf bundle if available:

- `figures/04_topics_problems.png`
- `figures/06_key_trends.png`

The repo versions of `01_corpus.png`, `07_community_governance.png`, and `08_platform_shares.png` are also safe to replace with the full-resolution fixed files if you already have them locally. Do not change the filenames or LaTeX paths.

## Final Overleaf check

After pulling/importing the repo, compile `main.tex` and confirm:

- title is exactly `From Web(logs) to Web(AI): Questions, Platforms, and Methods across Twenty Editions of ICWSM`
- figures are sharp and not clipped
- no `?` cross-references
- no author identities/affiliations appear in the review version
- checklist follows references and precedes appendices
- no generated LaTeX artifacts or root `main.pdf` are committed

Do not redo the prose or analyses unless a concrete error is found. The manuscript decisions are frozen.