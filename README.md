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

# Things to know (in general) before diving in
Here are some pointers about, well, computers in general before you get too lost into the world of LaTeX. 

The first are paths. Typically all operating systems will have a GUI that lets you click through folders to access other folders or files. LaTeX, and mostly all code-written software don't have this. So instead of clicking your way through folders, you have to instead tell (aka manually type out) the path that you want to go to. Like a map, all directions are relative. The folder I am located in now is called a _root_ directory; however, your current root directory will change if you jump into another folder, in which case this new folder will be called your root directory. The computer also has a root and home directory. The computer's root directory consists of the essential software components such as software applications and app/user data. For Windows, the computers root directory is typically a disk partition, known as a drive, such as the _C:\\_ drive. The home directory is typically where the computer defaults your location to. You have no business in the computer's root directory, so instead they give you a home directory which contains your desktop applications, documents, images, etc.

To navigate through these directories is much like reading through a map. Depending on where you are in the map changes how you navigate to your next folder destination. Therefore there are two ways to approach file navigation. The first is relative, and the second is static. Relative navigation, which is commonly used in LaTeX documents, is to travel to the desired file by starting from where you are now. A static navigation will typically start at the computer's root directory, the very beginning of the line, and then travel to the file of interest. Therefore, it doesn't matter where you are now, because I'm telling you to start at the root, which we all know where it is, and then move to the file folder-by-folder.

In code lingo this means
* `.` = current directory
* `..` = the directory above me
* `/` = designates a folder (note that Windows does the opposite `/`, we will not use this notation as its confusing and not conventional, and is reserved for calling functions in LaTeX)

Say we have a folder structure that has 4 separate folders illustrated below, where the root folder is the folder containing all the directories below.

![](./_images/file_h_temp.PNG)

Let's say I am currently in the main folder, and I want to travel to the images folder to check out an image. In order to do that relatively I would type 

```bash
../images
```

Which means from where I am now (_main_) I want to move up one folder (`..`), then down into the next folder (`/`) called _images_. Say I want to do this statically, such that I don't care where we are. I would instead write

```bash
C:/Users/GeorgeSun/Thesis/images
```

In this case I start at the very tip (_root_) and travel my way down to the _images_ folder. Quite a lot of typing, so we rarely use static navigation. Alternatively, if I want to share with you my files, these navigations would break, as your file system may not contain the files I have, especially if your username isn't GeorgeSun.

One downside to relative imports is that it matters where you are located, and those navigations will break if you move somewhere else. So let's say I am in the _sections_ folder and I want to get a file in the main folder. In the same situation, let's say I am already in the main folder and want to grab a file in this same folder. You can write to separate code

If I am in the sections folder
```bash
../main/example_file.tex
```

If I am in the main folder (no need to move anywhere)
```bash
example_file.tex
```

Let's say I give you one constraint, and that is to say you have to write one navigation for either of these files. What do you do? One way is to make a static navigation, as it doesn't matter where you live; however this is not recommended. The other method is similar, and that is to go up as many directories as you can until you reach a "_root-like_" folder. Here's the answer, and then think about it

```bash
../main/example_file.tex
```

In this case, my "_root-like_" directory is the directory that contains all the folders listed, e.g. bib, images, main, sections. So the goal is to navigate to this _root_ directory (`..`) and down the path you want. If we test this out for both scenarioes, if I live in the sections directory, using the navigation path I move up one (the root directory) and then down into the \main directory where I can located example\_file.tex. If I live in the main folder, although somewhat redudant, I move up one directory to the root, and then back into main to then get example\_file.tex. So one path works for both cases, and this is a strategy used often in the LaTeX heiarchy structure. 

# Parts of a LaTeX document
To set your document up, there are some paths you need to be familiar with
- Setting up your document class
- Where is your preamble, titlepage, etc.
- Where are your images
- Where are your bibliographies
- Where are your subfiles (if any)

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

The `\documentclass[options]{class}` is extremely powerful when setting up your document. It comes with options and class parameters. Class documents relevant to scientific writers are:
* article : for scientific journals and reports
* report : for longer reports containing chapters, small books, or even a thesis
* book : for books

And the options class establish a ruleset that your document will follow unless overriden in the contents:
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

To avoid clutter, all packages can be collected into a _preamble.sty_ file which only holds package references and other modifications to the entire document class. To then use the _preamble.sty_ file into the actual document, you import the _preamble.sty_ file like any other package. Essentially, you are making one package that gets imported which imports all the packages you want. To do this you need two parts.

In the preamble header you write

```tex
\ProvidesPackage{preamble}
```

and in the document you import it as 
```tex
\usepackage{preamble}
```

## Images
As a general note, do not put spaces in any file you name, if possible. This is especially true for image names, since importing images from other files which contain spaces will lead to trouble. If you do have spaces in your images (again, try to avoid this), you can add a package called [grffile](https://ctan.org/pkg/grffile?lang=en) that will behind the scenes remove all spaces in your image file directories so you can use spaces in your image names. So in your preamble you should include

```tex
\usepackage[space]{grrfile}
```

To then tell

## Bibliogrpahy


## Breaking it down - subfiles
The [subfile package](https://ctan.org/pkg/subfiles) is extremely useful when writing multiple parts to your document. Instead of compiling the entire document which contains multiple sections such as the abstract, introduction, etc. You can seperate your document into individual pieces that can independently compile, and cross-reference other subfiles, without having to render the entire document. How this works is that you have a master (aka _main.tex_) tex file that contains all of the necessary working components such as the document class, preamble, and other pieces you want to have to customize your document. In main.tex you then call subfiles using `\subfile{/path/to/subfile}` that take the contents from the subfile, and literally copies them into the main document. Imagine the main.tex file being a linker that bridges all of the subfile documents together to make a whole paper.

Because the subfile is a package you need to import, your preamble should contain the usepackage statement `\usepackage{subfiles}` which is used by the main.tex file. Each subfile (e.g. abstract, background, etc.) then contains a reference to the main document by referencing the document class of the main.tex file. In addition, the main file should include a cross-referencing package `\usepackage{xr}` which allows multiple files to reference one-another, despite not being in the same physical document. To tell the _xr_ package where to look you provide an external document argument `\externaldocument{path/to/other/subfiles}`. As a naming convention, I put all `\externaldocument{}` statements into a separate file called _refextdoc.sty_ which is imported with the main.tex document, much like the _preamble.sty_.

```tex
\documentclass[/path/to/main]{subfiles}
\begin{document}
... content of subfile
\end{document}
```

There are multiple ways to breakdown the file structure of the main.tex and subfiles. Three are provided in this template, so pick which ever works for you.

### Method 1
<!-- ![](/_images/file_h_method1.PNG) -->
<div>	
<img align="right" src="/_images/file_h_method1.PNG">
</div>
The first method segregates all essential peices of the document, from the main folder which contains the main.tex folder along with personalization files such as the preamble, refextdoc, and the titlepage.
<br><br><br><br><br><br><br><br><br><br><br>

### Method 2
<div>	
<img align="right" src="/_images/file_h_method2.PNG">
</div>
The second method is similar to the first, but the sections and main document are in the same folder. Referencing becomes much easier, however there is more visual clutter, and personally some may have a preference of physically segregating subfiles from the main file
<br><br><br><br><br><br><br><br><br><br>

### Method 3
<div>	
<img align="right" src="/_images/file_h_method3.PNG">
</div>
The easiet method to explain, but the least scalable. All the components of the document are in the main folder. Every section

## More advanced breakdown
Figures and tables are the visual meat of a paper or thesis. You will realize that you may have several figures and tables to make, and writing the code to justify figures, or creating tabular enviornments add a lot of visual noise to the actual content of your document. Therefore, figures and tables can be segregated from the main document, and even the subfiles themselves. As a general strategy, if you believe some peices of code are rarely changed once written, you can divorce those components into their own .tex document and include them in your subfile or main document when needed by placing this

![](/_images/file_h_tables_figures.PNG)

```tex
\input{relative path to table or figure}
```

For input files, you don't need to specify the document class or other parameters, LaTeX will literally copy the contents of the input file and place them where you evoked the `\input` method, as if you wrote it yourself.

# How to compile

## Basic compilation

## Bibliograph compilation