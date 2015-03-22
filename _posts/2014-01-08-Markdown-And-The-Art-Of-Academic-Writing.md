---
Date: 2014-01-08 14:10
Title: Scholarly Markdown and the art of academic writing (or how to put citations into markdown)
Category: Markdown, Publication, Academic, Citations, Collaboration
Tags: Markdown, Publication, Academic, Citations, Collaboration
layout: post
---

#URLs used:
* <http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown>
* <https://en.wikibooks.org/wiki/LaTeX/Mathematics>
* <https://hackage.haskell.org/package/pandoc-citeproc>
* <http://blog.martinfenner.org/2013/06/17/what-is-scholarly-markdown/>
* <http://blog.yoavram.com/citations-in-markdown-using-pandoc/>
* <http://2012-2013.chriskrycho.com/web/markdown-and-academic-writing/>
* <http://daringfireball.net/projects/markdown/>
* <http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown>
* <http://hackage.haskell.org/package/pandoc-citeproc>
* <http://www.surefoss.org/publishing-publizieren/all-you-need-is-text-markdown-via-pandoc-for-academia/>
* <http://blog.martinfenner.org/about.html>
* <https://github.com/karthik/markdown_science>


#Discussion
I've been getting into [markdown](http://daringfireball.net/projects/markdown/) as a generic writing tool. This blog uses markdown and I've been using markdown within Ipython and the [github hosted publically shared derivatives](http://nbviewer.ipython.org/gist/AntArch/8315767). Basically it's quite nice. It's a simple text format that's a bit more readable than latex (which is something I've been meaning to get around to for years but have never really sorted out). The problem with latex is that not many people in my domain (archaeology and geography) actually use it. Hence, as I want to use tools for dynamic collaboration - latex is quite simply a battle that is unlikely to be won as I won't be able to get everyone to convert to using it.

Markdown is simpler.  The readable text element means that you can author documents using realtime collaboration environments like **Google Docs** or **etherpad**. 

However, in order to be useful in a scholarly setting markdown also needs to employ other functionality, most notably referencing. This has been recognised by the [Scholarly Markdown Group](http://blog.martinfenner.org/2013/06/17/what-is-scholarly-markdown/) who have set up a [Markdown Science github repository](https://github.com/karthik/markdown_science) and the the community who've built extensions for markdown. One of the most complete extensions is [Pandocs Markdown](http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown).

#Pandoc
Pandoc is a Haskell library for converting from one markup format to another, and a command-line tool that uses this library. It can read:

* markdown 
* Textile
* reStructuredText
* HTML
* LaTeX
* MediaWiki markup
* Haddock markup
* OPML
* DocBook; 

and it can write:

* plain text
* markdown
* reStructuredText
* XHTML
* HTML 5
* LaTeX (including beamer slide shows)
* ConTeXt
* RTF
* OPML
* DocBook
* OpenDocument
* ODT
* Word docx
* GNU Texinfo
* MediaWiki markup
* EPUB (v2 or v3)
* FictionBook2
* Textile
* groff man pages
* Emacs Org-Mode
* AsciiDoc and Slidy
* Slideous
* DZSlides
* reveal.js or S5 HTML slide shows 

It can also produce PDF output on systems where LaTeX is installed.

#[Pandocs Markdown](http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown)
[Pandocs Markdown](http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown) contains extensions to markdown which can be interpretted by the pandocs document conversion framework. 

#My markdown usage conventions
Here are my useage conventions. Most of these will be generic and will work whether it's in strict markdown or in pandocs markdown. Where there are signicant differences they will be noted.

##Headings
I use the # to determine heading and levels. The number of #'s determines the level of heading hierarchy. There is a blank 

#Inline formatting

##Lists
Ordered and unordered lists

###Unordered lists
Are basically bullet points. Each bullet point is denoted by an asterisk followed by a space at the beginning of a line '* '. The first point in a list must be preceded by a blank line. Indented bullets are prefixed by tabs to represent their indent level. For example:

* A single asterisk
	* An asterisk preceeded by a tab
		* An asterisk preceeded by two tab

###Ordered lists
Ordered lists are where numbers are used instead of bullets. Each bullet point is denoted by a number (note: it can be any number), followed by a period and a space at the beginning of a line '* '.

9. A single number ('9')
9. A single number ('9')
	9. A single number ('9') preceeded by a tab
		8. A single number ('8') preceeded by a tab
		7. A single number ('7') preceeded by a tab
	9. A single number ('9') preceeded by a tab

###Fancy lists (pandocs only)
Unlike standard markdown, Pandoc allows ordered list items to be marked with uppercase and lowercase letters and roman numerals, in addition to arabic numerals. List markers may be enclosed in parentheses or followed by a single right-parentheses or period. They must be separated from the text that follows by at least one space, and, if the list marker is a capital letter with a period, by at least two spaces.

The fancy_lists extension also allows ‘#’ to be used as an ordered list marker in place of a numeral:

#. one
#. two

##Links and references (not including citations)

###Bare urls
Just wrap the URL with a smaller than (<) and greater than (>) signs.

###Footnotes

##Illustrations and captions (captions are Pandocs only)
Pandocs

![Here is the caption](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Evidence_Based_Decision_Making_using_Open_approaches.svg/1052px-Evidence_Based_Decision_Making_using_Open_approaches.svg.png)

##Tables
I'm not sure if I would want to handcraft tables. My gut feeling is that tables are data and should come from data files

##Symbolic maths (pandocs only)
Mathematical notation is enclosed in dollar signs $. There should be no space after the first dollar sign and no space before the last dollar sign (this is so the parser knows the enclosed snippet is to be converted to maths symbols rather than two numbers expressed in US $)

There is a free online [book on mathtex](https://en.wikibooks.org/wiki/LaTeX/Mathematics)

$(x-y)/(y+z)$

$\forall x \in X, \quad \exists y \leq \epsilon$

###Symbols
$\forall x \in X, \quad \exists y \leq \epsilon$

###Greek letters
$\alpha, A, \beta, B, \gamma, \Gamma, \pi, \Pi, \phi, \varphi, \Phi$

###Operators
$\cos (2\theta) = \cos^2 \theta - \sin^2 \theta$

$\lim_{x \to \infty} \exp(-x) = 0$


$$\lim_{x \to \infty} \exp(-x) = 0$$

$a \bmod b$

$x \equiv a \pmod b$

###Powers and Indices
$k_{n+1} = n^2 + k_n^2 - k_{n-1}$

$\frac{n!}{k!(n-k)!} = {n \choose k}$

$\frac{\frac{1}{x}+\frac{1}{y}}{y-z}$

${n! \over k!(n-k)!} = {n \choose k}$

$^3/_7$

###Roots
$\sqrt{\frac{a}{b}}$

$\sqrt[n]{1+x+x^2+x^3+\ldots}$

###sums and integrals
$\sum_{i=1}^{10} t_i$
$$\sum_{i=1}^{10} t_i$$

$\int_0^\infty \mathrm{e}^{-x}\,\mathrm{d}x$

###Brackets, braces and delimiters
$( a ), [ b ], \{ c \}, | d |, \| e \|, \langle f \rangle, \lfloor g \rfloor, \lceil h \rceil, \ulcorner i \urcorner$

###Matrices and arrays
$\begin{matrix}
  a & b & c \\
  d & e & f \\
  g & h & i
 \end{matrix}$
 
##[References - Pandoc](http://johnmacfarlane.net/pandoc/README.html#citations)
References are the 'killer app' in order to make markdown a viable scholarly option. [References in Pandoc](http://johnmacfarlane.net/pandoc/README.html#citations) require a bibliographic reference source (either a link to a refrence file or embedded as indiviual references - both in the YAML section).

I haven't been able to get this to work so far :-(

Citations go inside square brackets and are separated by semicolons. Each citation must have a key, composed of ‘@’ + the citation identifier from the database, and may optionally have a prefix, a locator, and a suffix. Here are some examples:

	Blah blah [see @doe99, pp. 33-35; also @smith04, ch. 1].
	Blah blah [@doe99, pp. 33-35, 38-39 and *passim*].
	Blah blah [@smith04; @doe99].

A minus sign (-) before the @ will suppress mention of the author in the citation. This can be useful when the author is already mentioned in the text:

	Smith says blah [-@smith04].

You can also write an in-text citation, as follows:

	@smith04 says blah.
	@smith04 [p. 33] says blah.

Citations are created during parsing using the package [pandoc-citeproc](https://hackage.haskell.org/package/pandoc-citeproc). Using an external filter, pandoc-citeproc, pandoc can automatically generate citations and a bibliography in a number of styles. Basic usage is

	pandoc --filter pandoc-citeproc myinput.txt

If the style calls for a list of works cited, it will be placed at the end of the document. Normally, you will want to end your document with an appropriate header:

last paragraph...

	# References
The bibliography will be inserted after this header.

##Open Science extensions
What about ipython? Ipython notebook is a good way of publically sharing code with text markup as [I've shown](http://nbviewer.ipython.org/gist/AntArch/8315767). It is also a good way to pick up typos, errors and bugs and to share well documented exemplar code sequences. However, it's not a good way of collaboratively writing. In addition the Github for Markdown (GFM) markdown extension does not handle referencing. 

###Data
You can use [knitr](http://yihui.name/knitr/) for R. [Here is an example](https://github.com/articlemetrics/plosOpenR/blob/master/barPlotSummary.Rmd)
[reference][test]

Sweave

Pweave


###Code
What about syntax (github for markdown provides syntax flags)

###Metadata - Pandocs markdown
A YAML metadata block is a valid YAML object, delimited by a line of three hyphens (---) at the top and a line of three hyphens (---) or three dots (...) at the bottom. A YAML metadata block may occur anywhere in the document, but if it is not at the beginning, it must be preceded by a blank line.

Metadata will be taken from the fields of the YAML object and added to any existing document metadata. Metadata can contain lists and objects (nested arbitrarily), but all string scalars will be interpreted as markdown. Fields with names ending in an underscore will be ignored by pandoc. (They may be given a role by external processors.)

A document may contain multiple metadata blocks. The metadata fields will be combined through a left-biased union: if two metadata blocks attempt to set the same field, the value from the first block will be taken.

Note that YAML escaping rules must be followed. Thus, for example, if a title contains a colon, it must be quoted. The pipe character (|) can be used to begin an indented block that will be interpreted literally, without need for escaping. This form is necessary when the field contains blank lines:

---
title:  'This is the title: it contains a colon'
author:
- name: Author One
  affiliation: University of Somewhere
- name: Author Two
  affiliation: University of Nowhere
tags: [nothing, nothingness]
abstract: |
  This is the abstract.

  It consists of two paragraphs.
...


#Page layout in markdown

OK..... I've probably been a bit hard on Latex. Latex allows real control on pagination and output. However, to be brutally frank.... I don't care about that when I'm creating my document. On a collaborative paper I'm much more interested in the ability to manage content, words, references, footnotes, hierachies (heading 1....), data and images. Pagination is something the editor normally has to worry about!

That said, the [pandoc](http://johnmacfarlane.net/pandoc/) package handles document conversion beautifully. 
