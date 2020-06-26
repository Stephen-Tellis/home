---
layout: page
title:  "PDF Manipulation on Linux - The power user way!"
subtitle: 
date:   2020-06-27 21:21:21 +0530
categories: ["Linux"]
---

Time and again, Linux forums, have been flooded with the question, "What is the best way to manipulate a PDF?".   
Some might say use an online tool, but that has privacy concerns of its own, others my say it is [PDF Sam](https://pdfsam.org/ "Checkout PDF Sam"). While it is an absolutely wonderful tool with some nifty tricks up its sleeve, the question is, what it the "True **Power user** way of doing it?" or in other words, how do you do it plainly on the command line?   
Described below are two ways, one better than the other in its own way:
#### _Method 1:_
Ghostscript is a high-performance Postscript and PDF interpreter and rendering engine. Its conversion capabilities cover PDF, PostScript, PCL and XPS languages.
I found the usage to be pretty simple and straightforward with an exhaustive list of switches that let you do everything imaginable from viewing a preview, setting the render resolution to debugging tools. Find a comprehensive list [here](https://www.ghostscript.com/doc/9.52/Use.htm "Visit site").

Here is a small snippet I tried:   
Merge files in a folder:
```
gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -dPDFSETTINGS=/prepress -sOutputFile=merged.pdf File1.pdf File2.pdf
```
Mege files while preserving bookmarks:
```
gs -dBATCH -dDOPDFMARKS -dNOPAUSE -q -sDEVICE=pdfwrite -dPDFSETTINGS=/prepress -sOutputFile=merged.pdf mine1.pdf mine2.pdf
```
The best feature of ghostscript is that it comes pre installed with your installation and the second best is probably the switches. But, the only problem I had with it was its spped. IT IS SLOW!. Very SLOW and took up to a good 2 seconds to merge three files of about 2.5 MBs on my intel i7 machine. Those are unacceptale times.

#### _Method 2:_
This is a python package/library that nees to be installed. Donot fear, it takes commands directly from the terminal and doesnt require you to edit .py scripts to merge a file.
The package is aptly called [pdftools](https://pypi.org/project/pdftools/ "Go to site"). Installation is as easy as typing `pip install pdftools` in your terminal window.
The library can:
-   add, insert, remove and rotate pages
-   split PDF files in multiple documents
-   copy specific pages in a new document
-   merge or zip PDF files into one document  

Once installed go to the terminal and run:
```
pdftools -V
```
to check if the installation is working. Now you are good to go.
Here is a small snippet I used to merge two pdf files:
```
pdftools merge -o merged.pdf first_file.pdf second.pdf
```
I was extremely happy with the performance given that it is using python.
Although it covers the most basic features that are exected, it lacks the flexibility that Ghostscript offers. Lacking even some must have features such as merging bookmarks of the individual files.   

##### So which one is better? 
Well, there is never an easy answer, is there? Personally for me, not merging bookmarks is a make-or-break deal so I think will be sitcking to ghostscript for now.  
That being said, since I may contribute some bookmarks functionality to pdftools if I have some spare time in the near future. That should not be hard as PyPdf2 - the library wihich Pdftools uses, already supports bookmark manipulation.

{% comment %}
Might you have an include in your theme? Why not try it here!
{% include my-themes-great-include.html %}
{% endcomment %}

