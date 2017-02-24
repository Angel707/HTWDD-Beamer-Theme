# HTWDD-Beamer-Theme
An inoffizial presentation theme of the University of Applied Sciences Dresden (HTWDD) for LaTeX Beamer


## Background

This beamer theme is a custom theme, styled with simpliness in mind.
The design and first version without tikz was made by Hermann Lorenz.
This version was used in many student presentations between 2012 and 2014.
Angelos Drossos decided to refactor this theme using technics provided by tikz.


## Requirements

This beamer theme requires the TikZ (pgf) package to be able to compile.
The example representation is compileable with PDFLaTeX and LuaLaTeX.


## Usage

In the presentation, use the following command
between the \documentclass{beamer} command and the \begin{document} command
to enable the HTWDD beamer theme:

  \usetheme{HTWDD}

Keep in mind that the LaTeX compiler must be able to find the HTWDD beamer theme,
namely beamerthemeHTWDD.sty, beamercolorthemeHTWDD.sty, et cetera.

There are two major possibilities to install the HTWDD beamer theme:

  (a) Copy the theme files to your presentation folder,
      i.e. where your presentation.tex file is.
  (b) Install the theme files in any TeX search path folder,
      typically <HOME>/texmf.

Variant (a) is the easy and recommended method.
The section Installation (advanced usage) describes Variant (b) in more detail.


## Installation (advanced usage)

The first step is to find the texmf home directory (<TEXMFHOME>).
Typically, the texmf home directory should be one of the following paths:

 * ~/texmf (Linux)
 * C:/Users/<user>/texmf (Windows)

Most LaTeX distributions like TeXLive and MiKTeX include a path lookup tool
like kpsewich to find it:

 * kpsewhich -var-value=TEXMFHOME

Regarding MiKTeX, have a look at the section "Installing sty or cls files"
in the answer to the question "How can I manually install a package on MiKTeX (Windows)".

It is recommended to install the HTWDD beamer theme in its own subfolder,
e.g.:

 * <TEXMFHOME>/tex/latex/beamerthemeHTWDD/beamerthemeHTWDD.sty
 * <TEXMFHOME>/tex/latex/beamerthemeHTWDD/beamercolorthemeHTWDD.sty
 * <TEXMFHOME>/tex/latex/beamerthemeHTWDD/beamerinnerthemeHTWDD.sty
 * <TEXMFHOME>/tex/latex/beamerthemeHTWDD/beamerouterthemeHTWDD.sty

When the LaTeX compiler shows the following error message or something similar,

  ! LaTeX Error: File `beamerthemeHTWDD.sty' not found.

then the HTWDD beamer theme is not in any search path
used by the LaTeX compiler.


## License

This work may be distributed and/or modified under the conditions of
the LaTeX Project Public License, either version 1.3 of this license
or (at your option) any later version.
The latest version of this license is in
   http://www.latex-project.org/lppl.txt
and version 1.3 or later is part of all distributions of
LaTeX version 2005-12-01 or later.

This work has the LPPL maintenance status `maintained'.

The Current Maintainer of this work is Angelos Drossos.


## Questions and Contribution

If you want to contribute to improve or extend this theme,
write me, Angelos Drossos <dev.angelos.drossos@openmailbox.org>.
Questions are also welcome.
