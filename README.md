# Smart Water Networks TU Berlin Beamer Template

This repository contains the reusable TU Berlin Smart Water Networks Beamer
template and the final journal-club presentation for Rajabi et al. (2023).

## Files

- `main.tex`: example deck mirroring the six slides in the PowerPoint template.
- `journal_club.tex`: rubric-aligned 13-slide timed presentation plus five
  Q&A backup slides for Rajabi et al. (2023).
- `presentation_notes.md`: 11:30 speaking plan, balanced presenter allocation,
  transitions, and evidence-based Q&A preparation.
- `beamerthemeSmartWaterTU.sty`: reusable Beamer theme with the PowerPoint
  slide size, typography, title placement, footer logos, and slide numbering.
- `assets/`: extracted and converted graphics from the PowerPoint template.
- `paper-assets/`: local figure assets extracted from the supplied paper PDF
  for the journal-club presentation.
- `main.pdf` and `journal_club.pdf`: compiled outputs.
- `1-s2.0-S0043135423004487-main.pdf`: source paper.
- `OralExam_SlidesTemplate.pptx`: original presentation template.

Temporary extraction, rendering, comparison, and LaTeX build artifacts are
intentionally excluded from version control.

## Build

Use XeLaTeX or LuaLaTeX when available:

```sh
xelatex main.tex
```

Build the journal-club deck:

```sh
xelatex journal_club.tex
```

The template also has a pdfLaTeX fallback using Helvetica-compatible fonts:

```sh
pdflatex main.tex
```

The page size is fixed to the original 16:9 PowerPoint canvas:
`10in x 5.625in`.
