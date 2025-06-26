---
title: 'The Logistics of Starting a Paper'
date: 2025-06-23
permalink: /tips/paper/
author_profile: true
---

When you're ready to start writing an academic paper, it can feel a bit daunting, especially if you haven't worked with LaTeX or BibTeX yet.  Here are some guidelines to help you get started.  There are other ways to accomplish these same things, but I think these steps are the most straightforward.

First things first, I do NOT recommend using Overleaf to write a paper.  The version control functionality is simply not up to snuff.  You are far better off writing a paper in a git repository, which offers full version control.  Whether you are working alone or with collaborators, having a complete record of the entire writing process (including timestamps of who has made what changes) will make your life easier down the line.  It also makes my job easier as your advisor through this process.  I prefer writing in private repositories - although it helps us to see the whole messy process from start to finish, the rest of the world doesn't need all that information.

To start, create a new folder in your repository that will house your paper.  This folder should contain four things:

1. Your main paper `.tex` file, where you will actually write your paper.  I like to call mine `main.tex`, but any short-and-sweet name is fine.  Here is a template version that you can use to get started: [main.tex](/files/main.tex)

2. A `.bib` file to house all the BibTeX references cited within your paper.  Any time you cite a paper, add its BibTeX reference to this file.  Google Scholar has very useful functionality for this reference format; simply click the "Cite" button under a paper, then click the "BibTeX" option at the bottom left (although you should check these for accuracy).  Here's an example file with a single reference: [main.bib](/files/main.bib)

3. A style file that tells LaTeX how to format your citations.  You can use more complex style files that will format other parts of the paper (most journals offer their own style files that you can download from their websites), but I prefer this "vanilla" one: [jasa.bst](/files/jasa.bst)

4. A folder that will contain all the images used within your paper (nothing more and nothing less).  While these don't need to be in their own subfolder, I strongly recommend it.  It is worth the effort to keep your repository nice and tidy.

How Your Files Talk to Each Other
------

I prefer using the `natbib` package to integrate BibTeX and LaTeX.  First, add `\usepackage{natbib}` in the header of your `main.tex` file.  Then, if you have called your Bibtex file `main.bib` and your reference style file `jasa.bst`, then you simply need these two lines at the end of your `main.tex` file:

```
\bibliographystyle{jasa}
\bibliography{main}
```

Make sure these appear before `\end{document}`.  These two lines will tell your compiler to use the format of `jasa.bst` and the references within `main.bib`.


Compiling
------

Although many text editors offer their own compiling, it is useful to know how to compile your paper PDF directly from the command line.  First, navigate inside the folder where your paper files are stored.  Then (assuming you've used the aforementioned file names) run:

```
pdflatex main.tex
```

You may need to install the basic LaTeX package if your computer doesn't have it already (e.g., `brew install basictex` on Mac).  This command will create several helper files containing information on citations and labels/links within your paper (`main.aux`, `main.log`, etc.).  Running this command one time is NOT enough to generate the complete PDF.

Second, run:

```
bibtex main
```

This will get all of the information ready for the references within your paper.  This command will also output helpful warnings when references are missing or incomplete - pay attention to these and try to fix the problems.

Then, re-run:

```
pdflatex main.tex
```

Now that all the helper files have been generated, this command will provide the fully compiled paper with all references, citations, and internal links.  When you make changes to either `main.tex` or `main.bib`, I recommend re-running this whole trifecta (`pdflatex`, then `bibtex`, then `pdflatex` again).


Best Practices
------

Lucky for us, many papers on arXiv include their original source files.  You can download the `.tex` file of a paper by navigating to the paper's home page on arXiv (like [this one](https://arxiv.org/abs/2012.08015)) and clicking the "TeX Source" button in the upper right corner.  If you are ever stuck trying to do something in LaTeX (like formatting an equation/table/figure), just find a paper that did it well and check out their source code to see how they pulled it off.

Some other things to keep in mind:

* Push your work often!  Version control in the writing process is only as useful as you make it.
* Make sure you push every file that is needed to compile your PDF up to the repo.  This includes all images.  When I clone your repo, I should be able to run the above commands and regenerate the exact PDF that you have on your end.
* Do NOT push the compiler helper files to your git repository.  These files do not need version control, and they will just clutter up your repo.  If it helps, you can add the `.aux`, `.log`, and `.out` file extensions to your `.gitignore` file, so they will be automatically ignored.
* Do NOT push your compiled PDF to your git repository (for the same reasons).
* If you are working on a paper with others, make sure you are not working on it at the same time.  This can cause merge conflicts.  A simple message that says "Hey, I'm working on this paper this morning, I'll ping you when I'm ready to pass it back" is all it takes.



