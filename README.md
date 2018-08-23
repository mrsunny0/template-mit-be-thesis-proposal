# Introduction
There are two fundamental categories for digital document writing. The first is plain text, where formatting is done through symbolic representation and code. The second are word processors, documents that hide most to all of the formatting away from the user such that they experience an interface known as WYSIWYG (what you see is that you get), where bolded words are literally bolded on your document.

\LaTeX is the first flavor of document writing, a plain text format using markup tagging to define general structure and symbolism of a document. For example, \textbf{XYZ} means to bold 'XYZ'.

# Setting it up
There are two pieces to setting up LaTeX on your local computer
* A LaTeX compiler (for either Windows or Mac)
* Optional, although highly recommended, a LaTeX IDE (integrated development environment) where you can type and compile your code in one software enviornment (much like using Word).

## Downloads
* LaTeX compiler
	- Word: [MikTex](https://miktex.org/download)
	- Mac: [MacTex](http://www.tug.org/mactex/)
* LaTex IDE (in order of _my_ preference)
	- [TeXmaker](http://www.xm1math.net/texmaker/)
	- [TeXstudio](https://www.texstudio.org/)
	- [TeXworks](http://www.tug.org/texworks/) (this is automatically installed with most TeX compiler installations)

To avoid a long step-by-step guide on downloading these packages, I will instead refer you to easy to follow online videos, courtesy rof YouTube.
* For windows: [both MikTex \& Texmaker](https://www.youtube.com/watch?v=WnIYTFTsWiU)
* For mac: [mactex](https://www.youtube.com/watch?v=XlxiytGeWds) \& [texmaker](https://www.youtube.com/watch?v=-KgxKA-UBh4)

# The makeup of a LaTeX document
Setting aside the syntax and coding of a LaTeX document, let's learn more about how to structure the document. This is where most of the work comes into play when customizing a certain document style. The most basic layout will look like this

## The document class
```tex
\documentclass[a4paper]{article}

#... (preamble)

\begin{document}

#... (document content)

\end{document}
```

The `\documentclass[options]{class}` is extremely powerful when setting up your document. It comes with options and class parameters. Class documents relevant to scientific writers are
* article : for scientific journals and reports
* report : for longer reports containing chapters, small books, or even a thesis
* book : for books

And the options class establish a ruleset that your document will follow unless overriden in the contents
* 10pt, 11pt, 12pt, etc. font sizes
* a4paper, letterpaper, etc.
* twocolumn
* landscape

So for example I want to write a article in a scientific journal that requires 12 pt font, two columns, on default paper size (letterpaper), then your document class will look like

```tex
\documentclass[12pt, twocolumn, letterpaper]{article}
...
\begin{document}
...
\end{document}
```

## The preamble
The preamble contains all the packages that make your document either easier to write, or flashy when compiled. The preamble will typically contain a laundry list of `\usepackage[]{}` statements that will import packages that further customize your document. For example, the package [_mathtools_](), [_amssymb_](), and [_amsfonts_]() are all used to help generate nice looking math fonts and symbols. Typically your IDE (e.g. TeXmaker) will take care of downloading all the packages needed to render your document from the interent. However, if you are missing a package, you may need to manually download it yourself. To do so, you need to go directly to the tex compiler and tell it what package you need. 

Fortunately, all essential packages are located in the _preamble.sty_ file located in this repository. So feel free to add or subtract from that list to fit your needs

## Breaking it down - subfiles
The subfile package is extremely useful when writing multiple parts to your document

# Customizing your LaTeX document
To set your document up, there are some paths you need to be familiar with
- Where is your preamble, titlepage, and refextdoc
- Where are your images
- Where are your bibliographies
- Where are your subfiles (if any)