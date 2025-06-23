---
title: 'The Logistics of Starting a Paper'
date: 2025-06-23
permalink: /tips/paper/
author_profile: true
---

When you're ready to start writing an academic paper, it can feel a bit daunting, especially if you haven't worked with LaTeX or BibTeX yet.  Here are some guidelines to help you get started.

First things first, I do NOT recommend using Overleaf to write a paper.  The version control functionality is simply not up to snuff.  You are far better off writing a paper in a git repository, which offers full version control.  Whether you are working alone or with collaborators, having a complete record of the entire writing process (including timestamps of who has made what changes) will make your life easier down the line.  It also makes my job easier as your advisor through this process.  I prefer writing in private repositories - although it helps us to see the whole messy process, the rest of the world doesn't need all that information.

To start, create a new folder in your repository that will house your paper.  This folder should contain four things:

1. Your main paper `.tex` file, where you will actually write your paper.  I like to call mine `main.tex`, but any short-and-sweet name is fine.  Here is a template version that you can use to get started: [main.tex](/files/main.tex)

2. A `.bib` file to house all the BibTeX references cited within your paper.  Any time you cite a paper, add its BibTeX reference to this file.  Google Scholar has very useful functionality for this reference format; simply click the "Cite" button under a paper, then click the "BibTeX" option at the bottom left (although you should check these for accuracy).  Here's an example file with a single reference: [main.bib](/files/main.bib)

3. A style file that tells LaTeX how to format your paper.  Most journals offer their own style files that you can download from their websites.  I prefer this "vanilla" one: [jasa.bst](/files/jasa.bst)

4. A folder that will contain all the images used within your paper (nothing more and nothing less).  While these don't need to be in their own subfolder, I strongly recommend it.  It is worth the effort to keep your repository nice and tidy.

How Your Files Talk to Each Other
------

(TO DO)


Compiling
------

(TO DO)

Best Practices
------

* Do NOT push the compiler helper files to your git repository.
* Do NOT push your compiled PDF to your git repository.
* But DO make sure the repository houses all the necessary files for someone else to compile the PDF themselves.