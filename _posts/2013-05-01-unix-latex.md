---
layout: post
title: Latex tricks
tags: latex tricks unix documents
---
{% raw %}

Latex is pretty cool, I just don't know what profession uses Latex, but I wouldn't mind being  apart of that world.

## Layout

### Show the Boxes

Before you can start working on a docuemnt, you first must know where you are, and in order to do this, you must know what the layout looks likes. The first thing that you must is to show the boxes that you will be working, and this is done with the package `showframe`. This is how you do it

    \usepackage[texcoord,gridunit=cm]{showframe}

This will outline all the components of your document.

### Setting the size

This is the sizes that I have created for the MYRA docs:

    \usepackage[top=.24in, bottom=2in, left=.76in, right=1.24in]{geometry}
    \headheight = 1in
    \textheight = 7.76in
    \footskip = 0.5in

This will create a document that will work the the current MYRA standard.

## Scale all graphics

If you would like to scale all graphics on a document, add this to the preamble

    \let\oldgraphic\includegraphics
    \renewcommand{\includegraphics}[2][]{
      \oldgraphic[scale=.8]{#2}
    }

There is also an example of how to [resize images to full size of document (on StackExchange)](http://tex.stackexchange.com/questions/12459/resize-large-images-that-exceed-page-margin-whilst-respecting-existing-scale)

## Figures and Table

Figures and tables are inserted into the doc as floats. There are a number of ways that you can alter the way this will look.

    % Change the style of floats (add a border)
		\usepackage{float}
    \floatstyle{boxed}
    \restylefloat{figure}
    \floatplacement{figure}{h}

This will put a box around the float, and float it by using `h` which means here. For a full list of what your options are, check out [Wiki Books](http://en.wikibooks.org/wiki/LaTeX/Floats,_Figures_and_Captions#Figures)

### Tabular (or tables)

If you find that the rows of tables are falling off the site of the page, change them the width of the columns to force text wrapping (#textwrap).

## Putting a Part on a new page

Sometimes you would like to have your parts to start with a new page, this is how you do it:

    let\stdpart\part
    \renewcommand\part{\newpage\stdpart}

Remember that a *part* is like a section, or a header.

## Fonts

According to the documentation on [wikibooks](http://en.wikibooks.org/wiki/LaTeX/Fonts), you can use any installed on  your system if you install the package `fontspec`. Here is how you do it


    \documentclass{article} 
    \usepackage{fontspec}
    \setmainfont{Arial}

    \begin{document}
    Lorem ipsum...
    \end{document}

To see a list of fonts on the system, run `fc-list :outline -f "%{family}\n"`.

### Use standard fonts

There are some standard fonts available already install into texlive. To use them, 

There are a number of fonts already in the system, and you can change the default by adding this to the LaTeX file.

    \renewcommand{\sfdefault}{phv} 
    \renewcommand{\familydefault}{\sfdefault}


Available Fonts include:

Family                  Font Name
-------------------     -----------------------------
pag                     Avant Garde
fvs                     Bitstream Vera Sans
pbk                     Bookman
bch                     Charter
ccr                     Computer Concrete
cmr                     Computer Modern
pcr                     Courier
mdugm                   Garamond
phv                     Helvetica
fi4                     Inconsolata
lmr                     Latin Modern
LinuxBiolinumT-OsF      Linux Biolinum (used to be 'fxb')
LinuxLibertineT-OsF     Linux Libertine (used to be 'fxl')
pnc                     New Century Schoolbook
ppl                     Palatino
ptm                     Times
uncl                    Uncial
put                     Utopia
pzc                     Zapf Chancery

## Headers and Footers

Adding headers and footers can be a little difficult, but here is a couple of things that make them look really good

This will require you to set a color: `\definecolor{cool-beans}`, see `color` below

    % Set the footer
    \fancyhead{} % clear all header fields
    \fancyhead[LE,RO]{\@title}
    \fancyhead[RE,LO]{\includegraphics{Myra-logo-small.png}}
    \renewcommand{\headrulewidth}{2pt}
    \renewcommand{\headrule}{\hbox to\headwidth{%
      \color{cool-beans}\leaders\hrule height \headrulewidth\hfill}
    }

    \fancyfoot{} % clear all footer fields
    \fancyhfoffset[R]{0in}
    \renewcommand{\footrule}{\hbox to\headwidth{%
      \color{cool-beans}\leaders\hrule height \headrulewidth\hfill}
    }
    \renewcommand{\footrulewidth}{2pt}
    \fancyfoot[LE,RO]{Page \thepage{}  of \pageref{LastPage}\\\@date}
    \fancyfoot[RE,LO]{\@title\\\@author}
{% endraw %}
