
# LaTeX Beamer template
This is a [LaTeX](https://www.latex-project.org/) [Beamer](https://ctan.org/pkg/beamer?lang=en) template for making NRCan slide decks, but
using LaTeX.
It uses background images extracted from the NRCan PowerPoint deck.



# Files

You need the following files for this template to work:

1. `nrcan_template_base.tex`
2. `nrcan_content.jpg`
3. `nrcan_lastpage.jpg`
4. `nrcan_title.jpg`

# How to use
Add the following after your `\documentclass` line in your LaTeX file:
```tex
\input{nrcan_template_base}
```

**NB**: This template is designed to work with the Beamer 16:9 aspect
ratio, so you should add this to your Beamer artuments.
For example: 
```tex
\documentclass[11pt,aspectratio=169]{beamer}
```

## Frame (slide) Enviroments and Commands
There are four NRCan-specific frame environments or commands available:

### 1 `\nrcanTitleframe` (command)
This makes a title page using the NRCan background graphic.
Uses the usual Beamer title information, which must be defined in the
document preamble (before `\begin{documents`).
Example from `example.tex`:
```tex
\title{This is the title}
\author{Author here}
\institute 
{
  Title\\
  Division/Sector\\
  Natural Resources Canada
}
\date{Venue\\
     \today}
.
.
\begin{document}
%% Title page
\nrcanTitleframe
```

### 2 `nrcanframe` (environment)
This is for normal content pages and uses the appropriate NRCan
background graphic.

Usage:
```tex
\begin{nrcanframe}
% slide content here
\end{nrcanframe}
```

### 3 `\nrcanGraphicFrame` (command)
This is a frame command for creating a frame (slide) for a single
graphic from a single image file.
All content is passed in to the command through four arguments:

1. Title
2. Graphic file, passed to `\includegraphics`
3. Arguments for `\includegraphics` (usually width, height)
4. URL source for graphic

Here is an example from example.tex

```tex
\nrcanGraphicFrame
  {Wikipedia - map of Canada}                                       % arg0 - Title
  {680px-Map_Canada_political-geo}                                  % arg1 - graphic file
  {height=\paperheight/5*4}                                         % arg2 - \includegraphics arguments
  {https://en.wikipedia.org/wiki/File:Map_Canada_political-geo.png} % arg3 - url source of graphic
```

### 4 `\nrcanLastFrame` (command)
This prints the last slide of the page, with the Canada word mark in
the middle of the page (uses `nrcan_lastpage.jpg` as the page background).

# Example
The file example.tex shows how to use the template, producing example.pdf.

# Dependencies
- [Beamer](https://ctan.org/pkg/beamer?lang=en)
- [calc](https://ctan.org/pkg/calc?lang=en)
- [hyperref](https://ctan.org/pkg/hyperref?lang=en)
- [tikz](http://mirrors.ctan.org/graphics/pgf/base/doc/pgfmanual.pdf)


# Copyright

Copyright 2021 Glen Newton

Except for the following files, which are Copyright (c) Natural
Resource Canada:

* `nrcan_title.jpg`
* `nrcan_content.jpg`
* `nrcan_lastpage.jpg`

And, [`680px-Map_Canada_political-geo.png`](https://en.wikipedia.org/wiki/File:Map_Canada_political-geo.png), used in the example, is in
the public domain.


# TODO 

1. French version derived from french PowerPoint template
2. Make into a proper Beamer style
3. Move page numbers to upper right hand corner
4. ~~Add page numbers to `nrcanGraphicFrame`~~
