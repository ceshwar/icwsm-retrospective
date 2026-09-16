# Handoff: finish ICWSM Overleaf/GitHub project

Repo: https://github.com/ceshwar/icwsm-retrospective
Branch: `main` (default branch)
Current latest commit at handoff: `7f0ff746b818c4477bc231bdf72d9b231c4bd347`

## What is already committed

- `.gitignore` was committed first and excludes LaTeX build artifacts and root compiled PDFs.
- Exactly one root `.tex` file exists: `main.tex`, containing `\documentclass`.
- All manuscript section/table `.tex` files are under `sections/`.
- `references.bib` is included for editing/reference.
- `sections/references.tex` is currently input directly by `main.tex`, so a BibTeX-generated `.bbl` does not need to be committed.
- The final prose pass is incorporated, including:
  - chosen title: `From Web(logs) to Web(AI): Questions, Platforms, and Methods across Twenty Editions of ICWSM`
  - stronger punchline and framing
  - Section 5 AI bridges
  - selective de-hedging
  - platform-composition limitation
  - fixed-length and strict-governance checks
  - release language says materials/code will be released **upon publication**, not during review
  - AI disclosure and ICWSM checklist
- No compiled manuscript PDF has been intentionally committed, following the requested `.gitignore` convention.

## Still required before Overleaf will compile

### 1. Add the AAAI style file
Copy the known-good `aaai2026.sty` from the latest local/Overleaf source bundle to the repository root:

`aaai2026.sty`

Do not modify it.

### 2. Add the five figure files
Create `figures/` and add these exact filenames from the latest local source bundle:

- `figures/01_corpus.png`
- `figures/04_topics_problems.png`
- `figures/06_key_trends.png`
- `figures/07_community_governance.png`
- `figures/08_platform_shares.png`

Use the latest fixed versions. In particular, Figure 2 / `06_key_trends.png` should use the corrected range that does not clip the bands, and Figure 3 / `07_community_governance.png` should be the fixed version from the final local bundle.

### 3. Compile and fix only blockers
Run from repo root:

```bash
latexmk -pdf main.tex
```

If `latexmk` reports a missing package/style/input, add only the missing source asset. Do not redesign/rewrite unless compilation exposes an actual problem.

Check for:

```bash
grep -E "Undefined control sequence|LaTeX Error|Citation.*undefined|Reference.*undefined|Overfull" main.log
```

The manuscript previously compiled cleanly from the local bundle, so remaining issues should mostly be missing repo assets.

### 4. Verify layout quickly
Open `main.pdf` locally and confirm:

- title is exactly the chosen Web(logs)/Web(AI) title
- main paper + references end by page 11
- ICWSM checklist begins after references and before appendices
- figures are not clipped
- no `?` cross-references
- no author identities/affiliations appear in the review version
- no stale mental-health checklist text

### 5. Do NOT commit generated LaTeX artifacts
Do not commit:

- `*.aux`
- `*.bbl`
- `*.blg`
- `*.fls`
- `*.fdb_latexmk`
- `*.log`
- `*.out`
- `*.synctex.gz`
- `*.run.xml`
- `*.bcf`
- root compiled PDF (`main.pdf`)

Figure PDFs would be okay under `figures/`, but current figures are PNGs.

## Important manuscript decisions already frozen

- Keep the title exactly as it is.
- Keep `Platforms change; the questions recur.` as the recurring punchline.
- Do not add new substantive analyses unless required to fix an incorrect claim.
- Do not broaden the empirical claim beyond what the community/governance case supports.
- The corpus, derived measurements, analysis code, and documentation are **not available during anonymous review** and are described as being released **upon publication**.
- Do not re-introduce unfinished Appendix G / review-pending bibliography material.
- Avoid AI-writing tropes during any emergency prose fix: no repetitive `not X, but Y`, excessive signposting, generic three-part lists, or layers of qualification around simple claims.

## If time is extremely short

Priority is:

1. add `aaai2026.sty`
2. add the 5 figures
3. `latexmk -pdf main.tex`
4. fix only compile errors / missing references
5. visually inspect pages 1, figure pages, page 11, checklist start, and final appendix page

The source text is already in GitHub. Do not spend time redoing the prose pass.
