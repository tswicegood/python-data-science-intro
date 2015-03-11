---
layout: page
title: Introduction to the Tools
---

Every new discipline has tools that you need to be familiar with to get started.
Those tools for data science in Python are [Anaconda][] and
[IPython Notebooks][].  This section introduces you to those tools.


## Anaconda

Much of the scientific Python stack requires complicated, compiled code to run.
Normal installation methods require you to compile tools like [Numpy][] and
[pandas][] on your computer before you can use them.  Anaconda is a distribution
of Python that comes with all of these tools ready to use.

Anaconda ships with a tool call [`conda`][conda] for managing your local
packages and updating your code. We're going to create an environment to do
all of our work in:

```console
$ conda create --name nicar anaconda python=2
... output from conda ...
$ source activate nicar
(nicar) $
```

If you're on Windows, you don't have to include the `source`.

Now you have an environment that includes the entire Anaconda stack inside it.

> There's a lot more that conda can do, including exporting environments for you
> to share with others, building packages, and more.  Rather than dive into
> those, we'll leave that as an exercise for the student.  A great place to
> start is [conda.io][conda].


### Quick Note on `pip`

You can install *most* data science packages from Python using `conda install`.
You might come across a new package or something not specifically related to
data science that you can't install using `conda`.  When that happens, you can
rely on the standard Python installer: `pip`.  It's automatically available in
any conda environment that has Python installed.  If you somehow end up with an
environment that doesn't have it installed, you can install it via `conda
install pip`.

Also, if you don't want to try the Anaconda distribution, you can still work with iPython, pandas and bokeh.
You can install each of them via pip in your own virtualenv:

```pip install ipython pandas bokeh```

This will handle all of the dependencies for pandas, but you will need to have a compiler installed. On a Mac,
you can install the Command Lines Tools for XCode by downloading it at [Apple's developer site].


## IPython Notebooks

A key companion to any scientist is their notebook.  It's the place where they
work out their ideas, flesh out theories, and plan experiments.  Their killer
feature is that they can be shared and read by other scientists.

Like their analog counterparts, IPython notebooks (often referred to as `ipynb`
files) allow you to capture your thoughts in one place including code that can
be executed again and the output of them.

Let's get started.  The first thing we need to do is create a directory where
we can store all of our work.  I'm going to call my directory `notebooks` in my
home directory.  You can name it whatever you'd like, but if you use a different
name, make sure to adjust the commands appropriately.

```console
(nicar) $ mkdir notebooks
(nicar) $ cd notebooks
(nicar) ~/notebooks/ $
```

Now that you have that directory created, it's time to create your first
notebook.  From the command line, run this command:

```console
(nicar) ~notebooks/ $ ipython notebook
# TODO include output
```

Your default web browser should launch and load up `http://localhost:8888/tree`.
It should look like this:

> **TODO Screen Cap**

Let's create a new one.  Click on the `New Notebook` button in the upper right.

> **TODO Screen Cap**


### Notebook Basics

This new interface is the place where all of your work is going to take place.
Each notebook is made up a collection of cells.  You can run each cell
individually or in combination with other cells.  Let's start with the basics
and have it say hello world:

```python
print("Hello, World!")
```

Click the play button in the toolbar that cell will run and display the result.

> **TODO Screen Cap**

Notice that the empty brackets over to the left now have a `1` in them.
That's to show you how many commands have been run in this notebook.

Once you create a cell and run it, you can go edit it, then re-run it.  Click
on the `print` statement again and edit it to simply assign a variable:

```python
who = "World"
```

Click play again and notice that the `1` changes to a `2` and the output went
away.  The output disappeared because there is no output when you assign a
variable.  Go back and edit the cell again to include the variable `who` on a
line by itself, then re-run it.

```python
who = "World"
who
```

This shows two things:

* Variables by themselves are outputted if they're the last item in the cell
* Each cell can be multiple lines!

Now let's go down to the cell below our first one and add another `print`
statement like this:

```python
print("Hello, {}!".format(who))
```

This time when you click play on this cell, you notice that it pulls the
variable `who` from the first cell and uses it inside the `print` function.
Variables are shared throughout a notebook the same way they are when you write
a script into a single file.


### Other Types of Cells

You're not limited to just Python in the cells. Through the magic of iPython, you can use bash commands like ```ls``` to list the contents of a directory or ```cd ..``` to navigate to another folder. 

Or you can keep track of notes using
[Markdown][]. To do that, select the current empty cell below your code, then
select the dropdown from the toolbar that says `Code` and switch that to
`Markdown`.  There you can add whatever you like:

    # Notes!

    This is plain Markdown text.  You can place [links][1], *emphasis*,
    and so on.  When you render this block by hitting the play button it
    will render as full Markdown.

    [1]: http://github.com/

Now, you're ready to start [exploring data with pandas].

[Anaconda]: http://continuum.io/downloads
[conda]: http://conda.io/
[IPython Notebooks]: http://ipython.org/notebook.html
[Markdown]: http://daringfireball.net/projects/markdown/syntax
[Numpy]: http://www.numpy.org/
[Pandas]: http://pandas.pydata.org/
[exploring data with pandas]: ./pandas.html
[Apple's developer site]: https://developer.apple.com/downloads/