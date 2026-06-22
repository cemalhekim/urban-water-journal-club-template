# Smart Water Networks TU Berlin Beamer Template

This folder contains a LaTeX/Beamer recreation of
`OralExam_SlidesTemplate.pptx`.

## Files

- `main.tex`: example deck mirroring the six slides in the PowerPoint template.
- `journal_club.tex`: detailed 19-slide journal-club presentation for
  Rajabi et al. (2023), designed for a 12-minute talk.
- `beamerthemeSmartWaterTU.sty`: reusable Beamer theme with the PowerPoint
  slide size, typography, title placement, footer logos, and slide numbering.
- `assets/`: extracted and converted graphics from the PowerPoint template.
- `paper-assets/`: local figure assets extracted from the supplied paper PDF
  for the journal-club presentation.
- `main.pdf` and `journal_club.pdf`: compiled outputs.

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
