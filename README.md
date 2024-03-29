# LaTeX Template for Scientific Theses ![Build Status](https://github.com/latextemplates/scientific-thesis-template/workflows/Build%20with%20lualatex/badge.svg)

> This template is a general template for scientific theses.

Currently, it is the unofficial LaTeX template for Master, Bachelor, Diploma, and Student Theses.

See [docs/](docs/) or <http://latextemplates.github.io/scientific-thesis-template/> for a documentation of the template.

## License

The license of this work is [CC0](https://creativecommons.org/publicdomain/zero/1.0/), which corresponds to "public domain".

### Exceptions

The images in `logos` are subject to other copyright from other parties:


### Recommended setup of MiKTeX
* Install MiKTeX for: "Only for: `username`"
* Install MiKTeX to: `C:\MiKTeX`. This enabled browsing for documentation at `C:\MiKTeX29\doc\latex
* Install missing packages on the fly: `Yes`

Characteristics of the template
-------------------------------
* UTF-8
* pdflatex
* [latexmk]
* [biblatex]+[biber] instead of plain [bibtex]

This template works on Windows using the current [MiKTeX](http://www.miktex.org) distribution.
On Linux (TexLive full >= 2013) should work without any issues.
Even though AuToLaTeX is [more powerful than latexmk](http://www.arakhne.org/autolatex/), it is [not included in MiKTeX](http://www.ctan.org/pkg/autolatex) and therefore it is not used here.


Using with your own git repository
==================================

Initialization
--------------
This howto assumes that you have not a git repository for your thesis.
If you have, just add https://github.com/latextemplates/uni-stuttgart-computer-science-template.git as upstream and merge the branch "template" into your "master" branch.

1. Open command line
1. Change to the directory where you want to have your main tex file.
1. Fetch the template from github: `git clone https://github.com/ISTE-RSS/template-thesis.git`.
1. Rename `origin` to `github` to enable adding your own `origin` repository: `git remote rename origin github`
1. Create a new branch master starting from the latest commit in the `template-rss` branch: `git checkout -b master`

Now, you are on the `master` branch, where you can write your thesis and push it to your (remote) `origin` repository, in case you have one.

Merging updates from the template
---------------------------------
If you want to merge updates from github, do the following:

1. git fetch github
1. git merge github/template-rss


LaTeX compilation
=================
The template is compiled using normal LaTeX commands.
Your LaTeX environment (such as [TeXStudio]) should take care about the compilation transparently.
When the "Package Installation" dialog pops up at TeXStudio, choose your username at "The package will be installed for:" and uncheck "Always show this dialog before installing packages."
If you want to include .svg graphics, [inkscape] has to be in your path.

If you want to compile using the command line, you can use following tools.

Automatic compilation using latexmk
-----------------------------------

    latexmk main-english

Continuous previewing using latexmk
-----------------------------------

    latexmk -pvc main-english

This will open a [Sumatra PDF] and only works with the supplied configuration.

### latexmk configuration
This repository ships a `.latexmk` which is read by latexmk.
It is configured for Windows and especially sets Sumatra PDF as default PDF viewer.
You can make this local configuration a global configuration, when you put it at [the right place](http://tex.stackexchange.com/a/41149/9075).

If you want to add more packages, configure it there.
For instance, for support of makeglossaries see http://tex.stackexchange.com/questions/1226/how-to-make-latexmk-use-makeglossaries.

Automatic compilation using make
--------------------------------
For those, who have [cygwin](http://www.cygwin.com/) installed or run a linux machine, this template offers a simple LaTeX makefile.
It is not so sophisticated as other projects, but does its job.

    make

Make targets:
 * `pdf` (default): Generates ausarbeitung.pdf
 * `aspell`: Checks all files using aspell.
 * `clean`: Removes all temporary files.
 * `mrproper`: Cleans up and removes also editor backup files.
 * `stand`: Creates a new PDF with the current status of the thesis.
 * `view`: Opens the configured viewer
 * `6`: Generates a 3x2 postscriptfile using psnup.

Alternatives:
* https://github.com/akerbos/ltx2any
* https://github.com/shiblon/latex-makefile
* https://github.com/ransford/pdflatex-makefile
* https://github.com/brotchie/latex-rubber-makefile
* [LaTeX-Mk](http://latex-mk.sourceforge.net/)
* See also http://stackoverflow.com/questions/1240037/recommended-build-system-for-latex and http://tex.stackexchange.com/questions/40738/how-to-properly-make-a-latex-project

Tweaks
======

Define Title, Author, ..
------------------------

The file `main-english` contains properties like title, author, thesis number, etc. Author and title can be set as commands to be able to reuse them (e.g., for the PDF properties).
* \newcommand{\docauthor}{Author's name}
* \newcommand{\doctitle}{Thesis title}

Change Appearance of Chapter Headings
-------------------------------------


Final version
-------------

  - If you included some version control statements, please remove them. Currently, the template does not support any, but it used to support SVN.
  - By using `\largeparge` and `\shortpage`, single lines at the bottom or at the top of the page can be manually fixed.
  - Search the PDF for "TODO" or similar things. Remove `\usepackage{todonotes}` in `preambel/packages_and_options`.
  - Ensure that you run `pdflatex` at least three times and that there no "undefined references".
  - The margins are intended for a duplex printing. **Do not change them** (or do exactly know what you are doing).

Further Reading
---------------

See http://wiki.flupp.de/LaTeX


# Contained Files and Directories

* main-english.tex
  * Main file
  * New chapters are added by using `\input`
* Makefile: The Makefile.
* README.md: This file.
* uni-stuttgart-cs-cover.sty: Verbatim copy of uni-stuttgart-cs-cover.sty available at https://github.com/latextemplates/uni-stuttgart-computer-science-cover
* `bibliography.bib`. Bibliography. [biblatex] format. Manage it with [JabRef].
* content/: Place for the actual content
  * content/introduction.tex: First chapter: The introduction
  * content/chapter2.tex: Second chapter
  * content/chapter3.tex: Related work
  * content/conclusion.tex: Conclusion and outlook.
* graphics/: Directory containing the figures.
  By using PDFLaTeX it is possible to use PDFs, JPGs, PNGs, ... We recommend to use PDFs to enable smooth scaling.
* commands.tex: File for macros.
  * commands.tex: Example macros

 [biber]: https://www.ctan.org/pkg/biber
 [biblatex]: http://tex.stackexchange.com/tags/biblatex/info
 [bibtex]: https://www.ctan.org/pkg/bibtex
 [inkscape]: http://inkscape.org/
 [JabRef]: http://jabref.sf.net
 [LanguageTool]: https://languagetool.org/
 [latexmk]: http://tex.stackexchange.com/tags/latexmk/info
 [overleaf]: https://www.overleaf.com/
 [Sumatra PDF]: http://blog.kowalczyk.info/software/sumatrapdf/free-pdf-reader-de.html
 [TeXstudio]: http://texstudio.sourceforge.net/

