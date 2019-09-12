# Introduction to LaTeX

## What is LaTeX?
LaTeX is a markup style document preparation system designed for text and mathematical formulas. Unlike other typesetters, like Word, LaTeX uses a plain text format that must be compiled into a pdf for other format. It is widely used in academia, hence we are covering it herre.

## How to write and compile LaTeX?
Since LaTeX is written in plain text format, you can write LaTeX files using any of your favorite text editors, like Vim or Sublime or whatever. LaTeX files have the extension `.tex`. In order to compile tex file into pdfs or other formats, one must use a TeX distribution. The most popular of which are MikTeX (https://miktex.org/) and TeX Live (https://www.tug.org/texlive/). Both of these links have information about how to install them on your favorite OS. If you create a TeX file in a text editor and want to compile into a pdf in command line, both of these distributions have commands `pdflatex <file>.tex` which will build the file. Additionally, `Latexmk` has a similar command line interface (https://mg.readthedocs.io/latexmk.html). 

While compiling via the command line is a valid way to use LaTeX, many people prefer to integrated environments to write, compile, and often view the pdfs all in one place. Some popular such applications include:
* TexMaker - http://www.xm1math.net/texmaker/ 
    * Cross platform support
    * Integrated pdf viewer
    * Syntax highlighting and autofill
    * Automatically download packages
* TeXShop - https://pages.uoregon.edu/koch/texshop/
    * Mac OS
    * Simple
    * Syntax highlighting
    * Pdf viewer
* Overleaf/ShareLaTeX - https://www.overleaf.com/ https://www.sharelatex.com/
    * Cloud based client
    * Allows for collaboration and sharing
    * Real-time preview
    * Syntax highlighting and autofill
    * Built in templates
    * No need to download packages
* LaTeXiT - https://www.chachatelier.fr/latexit/latexit-home.php?lang=en
    * Mac OS
    * Great for creating a single equation graphic for use in a non-LaTeX document
    * Can also generate entire documents
 
## Basics and Templates
A minimalistic LaTeX document must have a documentclass, and begin and end.
```latex
\documentclass{article}
\begin{document}
Hello World! % Comment
\end{document}
```
Commands start with backslash, `\`, curly braces surround arguments, and `%` starts a comment.

In order to format the page to meet submission requirements or to look a certain way, commands are put before the `\begin{document}` line. There are a lot of different options here, so I highly recommend starting with templates that look the way you want, as opposed to trying to set all of the options from scratch. A couple sites with good templates are:
* https://www.overleaf.com/gallery/tagged/academic-journal
* https://www.latextemplates.com/

In addition to standard homework or research paper styles, you can also use LaTeX to generate PDF presentations (using Beamer), posters, and more.

## Text
To separate paragraphs in LaTeX you need to include a blank line in between:
```latex
This is the first sentence in paragraph 1. This is the second sentence.
This is the third sentence.

This is the first sentence in paragraph 2.
```
For different text formatting things you can use commands like:
* `\textit{...}` - italics
* `\textbf{...}` - boldface
* `\textsl{...}` - slanted

## Lists
You can make lists with `itemize` and numbered lists with `enumerate`
```latex
\begin{itemize}
   \item Bullet 1
   \item Bullet 2
\end{itemize}

\begin{enumerate}
   \item Thing 1
   \item Thing 2
\end{enumerate}

```

## Math
To type math inline, use `$` to begin and end the math. For example:
```latex
Here is a sentence about the equation $Ax=b$ which is pretty important in all of math.
```
If you want to have equations in their own line, use the `align` command
```latex
\begin{align} % using {align*} wll remove numbering
   Ax &= b \\
   x_1 + x_2 &< 10 \label{eqn:mylabelname}
\end{align}
```
To start a new line, use `\\`. `&` aligns the `&`s on all lines. `\label{...}` creates a label attached to the equation, which allows you to reference the equation using `\ref{...}` or `\eqref{..}` in the text. The equation numbering and referencing are very convinient because they will automatically update when new equations are added, so you don't need to manually organize them. 

You can type pretty much any math symbol in LaTeX. A lot of them are pretty obvious, like `\psi` or a similar command works for Greek letter, `_` is subscript, and `^` is super script. There is a big list of them at http://web.ift.uib.no/Teori/KURS/WRK/TeX/symALL.html 
Here are some common examples:
* `\psi` - Greek letters
* `\left( stuff \right)` - Parentheses that auto size based on what is inside (also works with other kinds of brackets)
* `\frac{numerator}{denominator}` - Fractions
* `\int` - integral
* `\partial` - partial derivative
* `\sum` or `\prod` - sum or product
* `\leq` or `\geq` - less than or equal or greater than or equal
* `\in` or `\forall` or `\exists` - logical math symbols
* `\infty` - Infinity
* `\hat{x}` or `\dot{x}` or `\tilde{x}` for different formats on variables

Here is a tool to find the LaTeX command of a symbol you draw: http://detexify.kirelabs.org/classify.html
 
## Figures
As you would expect, you can include figures. I think the best way to explain this is with an example:
```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=6cm]{file.png}
    \caption{Put caption here}
    \label{fig:myFig}
\end{figure}
```
First, you must begin and end a figure with `\begin{figure}`. The `[]` section after that is used for setting the location. LaTeX generally tries to put the figure wherever it finds a nice spot to fit it. `[H]` puts it exactly where it is specified, but you can also set it to the top of a page, bottom of a page, in its own page, etc. `\centering` centers the figure. `\includegraphics{file.png}` is where the figure to be included in linked. The square brackets before that is where you can set the size of the figure to be included. `\caption{...}` put that text as a caption below the figure. `\label{fig:..}` works just like the equation above. You can use `\ref{fig:..}` to reference the figure and the figure number will automatically changed for you. The specifications of `fig:` and `eqn:` are not necessary if the label, but I find it makes it a lot clearer what you are referencing. A good resource for figures is: https://www.sharelatex.com/learn/Inserting_Images

## Page Formatting
Although this depends on the document type, you create sections in your pdf using the following commands, which do roughly what you would expect them to:
```latex
\chapter{Chapter Name}
\section{Section Name}
\subsection{Subsection Name}
\subsubsection{Subsubsection Name}
\paragraph
\subparagraph
```

## Packages
Many useful commands are not inherently build into LaTeX, so they must be loaded into using packages. Packages are included before the `\begin{document}` statement. The syntax for packages is:
```latex
\usepackage[options]{package}
```
Packages generally end in `.sty` and can be downloaded online. However, most of the LaTeX programmers will automatically download a package if you don't already have it. Most of the time when you are looking online for a command, it will mentione the package it is in, and a simple `usepackage` statement will do the job.
 
## Citations
LaTeX is also very convinient for easily including citations. They function similarly to references to equations or figures where you put `\cite{citationName}` in the text and it will automatically include the correct citation number. There are two main bibliography methods in LaTeX: BibTeX and theBibliography

For BibTex, create a separate plain text file with the extension `.bib` and put in citations in forms like
```latex
@book{golub2012matrix,
  title={Matrix computations},
  author={Golub, Gene H and Van Loan, Charles F},
  volume={3},
  year={2012},
  publisher={JHU Press}
}
```
The specific fields depend on the citation type, but this can easily be looked up. Additionally, these citations are automatically generated by Google Scholar and similar sites, so they can be easily copied in. To cite the above citation in you document, you would simply type `\cite{golub2012matrix}`. In order to compile these citations into the correct format, you will need a `.bst` file which contains the correct formatting for your needs. These are googleable for most standard formats. Then at the end of your document (before the `\end{document}` line) include the lines
```latex
\bibliography{format} % for style format.bst
\bibliography{myrefs} % for references in myrefs.bib
```
This has the advantage that you can set all the styling in the `.bst` file and it will format all citations the same. However, this can be a disadvantage as I find these style files difficult to modify.

The other method is thebibliography. For this, at the end of the document, put:
```latex
\begin{thebibliography}{1}
\bibitem{golub}
Golub, G. H., \&  Van Loan, C. F. (2012). \textit{Matrix Computations} (Vol..). JHU Press.
\end{thebibliography}
````
Then when you wish to cite this reference, use `\cite{golub}`. As you can see, you have to format each citation yourself, which can be a pain. However, it also gives you direct control over how the citation looks, instead of through a formatting file, which I often find easier. 

## Macros
LaTeX macros are commands you define yourself. They can be very useful for improving productivity and readability in your documents, because they save you from typing long commands over and over again. The syntax is:
```latex
\newcommand{name}[num]{definition}
```
An example of a macro I use is:
```latex
\newcommand{\pder}[2]{\frac{\partial {#1}}{\partial {#2}}}
```
The command creates a partial derivative when you type `\pder{u}{x}`. In the command, the first argument is the name of your command. The argument in the square brackets is the number of input arguments it takes (which are inputted in sets of curly braces.) The third argument is the definition of the function where `#1` and `#2` define where the input arguements go.

## Conclusions
In conclusion, LaTeX is very useful for typing equations and writing academic or mathematical materials. There are many great tools and resources out there to help you write LaTeX more efficiently and effectively. However, at the end of the day, it is basically a programming language, so you will likely end up Googling a lot of your questions and you will generally be able resolve all of them with Google's help (and the StackExchange: tex.stackexchange.com).

## Miscellaneous links
* Detexify (recognize unknown LaTeX symbols from a drawing): http://detexify.kirelabs.org
* TeXnique (LaTeX typesetting game): https://texnique.xyz
