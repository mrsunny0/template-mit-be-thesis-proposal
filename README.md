# TL;DR
Provided are templates for **MIT's Bioengineering Thesis Proposal**. Depending on your comfort, and level of LaTeX fluency there are three ways to approach a document that requires a large amount of labor and planning.

1. Write the entire latex document in one file: [link](https://github.com/mrsunny0/LaTeX-thesis-proposal/tree/master/Thesis%20Proposal-1-single_file).
2. Write the document piece-meal where parts of divided into sections that are then assembled into one major latex document: [link](https://github.com/mrsunny0/LaTeX-thesis-proposal/tree/master/Thesis%20Proposal-2-input).
3. Modularly break your latex document into compilable parts that each produce their own document, these documents are then assembled into a main document: [link](https://github.com/mrsunny0/LaTeX-thesis-proposal/tree/master/Thesis%20Proposal-3-subfiles).

Pros and cons for each strategy

| One main file | Divide into pieces | Divide into **compilable** peices |
| --- | --- | --- |
| One main file to manage and edit | Multiple files to edit | Multiple files to edit |
| Basic directory and file structure | Basic directory and complex file structure | Complex directory and complex file structure |
| Inevitably, the code will be gigantic | Divide-and-conquer approach, files are more manageable | Divide-and-conquer approach, files are more manageable and can be compiled separately |
| Longer the document, longer the compile time | Despite multiple files, the main document needs to be compiled each time | Each file can be compiled independently, and then assembled when ready |

# Table of Contents
- [TL;DR](#tl-dr)
- [Knowing your way (aka _paths_)](#knowing-your-way--aka--paths--)
  * [Navigation commands](#navigation-commands)
  * [Relative vs. Absolute paths](#relative-vs-absolute-paths)
  * [How LaTeX sees it](#how-latex-sees-it)
- [Different ways of management](#different-ways-of-management)
  * [Single file](#single-file)
  * [Divide-and-conquer](#divide-and-conquer)
  * [File hierarchy](#file-hierarchy)
- [Takeaway](#takeaway)

# Knowing your way (aka _paths_)

## Navigation commands

## Relative vs. Absolute paths

## How LaTeX sees it

# Different ways of management

## Single file

## Divide-and-conquer

## File hierarchy

# Takeaway
The major limitation is the length of code you need to edit and manage for such a long document. Initially, breaking the document down into pieces seems beneficial, but ultimately the time to compile becomes limiting as the _entire_ document needs to compile for every change. A solution that I have found efficient is to break down the document in such a way that _every piece can compile_ and render its own document, which can then be assembled. However, the downside is that the directory and path structure of your document becomes complex.
