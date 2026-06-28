# CLAUDE.md — IndiaMART MTP Thesis

Project context and working agreement for Claude Code. Read this first.

## What this project is
MTP thesis: **Recommendation Systems for IndiaMART**. Dept. of CSE, IIT Delhi.
Dual-degree (B.Tech + M.Tech). Supervisor: **Prof. Rahul Garg**. Full two-semester scope.
The deliverable is a LaTeX thesis compiled with **pdfLaTeX**.

## Structure decision
**Topical** organization — clean chapters per technique. NOT a phase-by-phase narrative.

## Repository layout
```
.
├── main.tex                # orchestrator; \newcommand metadata block at top
├── preamble.tex            # packages, IITD-style margins (1.5in left binding)
├── references.bib          # bibliography
├── chapters/
│   ├── 00_titlepage.tex
│   ├── 00_acknowledgements.tex
│   ├── 00_abstract.tex     # SCAFFOLD — write last
│   ├── 00_abbreviations.tex
│   ├── 01_introduction.tex # SCAFFOLD — write last
│   ├── ...                 # technique chapters added as decks are ingested
│   └── 99_conclusion.tex
└── figures/                # plots, diagrams (user supplies images)
```

## Build
```
pdflatex -interaction=nonstopmode main.tex
bibtex main
pdflatex -interaction=nonstopmode main.tex
pdflatex -interaction=nonstopmode main.tex
```
The preamble guards `lmodern`/`microtype` with `\IfFileExists` so it builds in minimal
environments too. Keep that guard.

## Metadata to fill (top of main.tex)
Full name as on records, entry number, supervisor, submission date. Everything else is wired.

## The deck → thesis pipeline (core workflow)
1. Decks are ingested **chronologically** (earliest semester first).
2. Per deck: extract topics → rewrite as **thesis prose** (not bullets) → flag figure/equation
   insertion points → assign each piece to a chapter.
3. After the first 2–3 decks, finalize the **topical chapter list** from actual content.
4. Reconstruct equations/diagrams as LaTeX/TikZ; leave `\includegraphics` placeholders for
   result plots the user will supply into `figures/`.

## Hard rules
- **Abstract, Introduction, chapter list are written LAST**, after content exists. Do not
  draft real versions early — it invents contributions and risks plagiarism.
- Two reference theses (Hiren Parmar; Ashish Choudhary) inform **structure/conventions ONLY**.
  Never reproduce their wording or specific phrasing. All technical content is the user's own.
- One chapter per file; keep sections independently editable.
- Prose over bullets in the thesis body, matching IITD CSE conventions.

## Style
Direct, concise, iterative. The user gives clear directional edits and prefers collaborative
refinement over long preambles.

## If an official IITD template appears
If the user adds an official department `.cls`/`.sty`, re-base onto that class file (keep the
per-chapter structure) rather than the hand-rolled preamble.
