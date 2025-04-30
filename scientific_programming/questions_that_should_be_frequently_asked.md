# Questions that *should* be frequently asked

## How do I transition between scripting and software development (Python edition)?
Scientific programming will involve both of these skills!
Projects are often started in Jupyter notebooks, where you can fiddle with functions and parameters and get rapid feedback, and when it comes time to write the paper, you'll probably use notebooks to make the figures.
But young scientists often rely too much on Jupyter notebooks, and don't know when it is time to start cleaning up and generalizing code.
So, here are some heuristics:

### Stage 1: Purely imperative in a Jupyter notebook
If you're not familiar with it, "imperative" coding is what we all start out doing: a bunch of lines of code in order that all execute, and variables are all in the global scope (that is, they are notebook variables that only go away when you restart the notebook).
It is normal for a lot of code to start this way, since it's the easiest to experiment with and change rapidly. 

If you are trying to quickly answer a question or see if a (small) step in the analysis works, this is the way to go.
Plotting will also (often) be imperative, though if you find yourself making similar plots repeatedly that can change.
Which brings us to the transition:

**How do I know it's time to switch to stage 2?**: *If you copy multiple lines of code between cells*, it's time to go to stage 2 and make a function out of them!

*Mini-tip:* you may try to avoid this point by taking a single cell and modifying it over and over again. 
If you're trying to get something working that's great, but *if the purpose of the cell is changing, make a new cell rather than changing the old one.*

*Documentation tip:* at this stage, the appropriate level of documentation is to write in-line comments for tricky or unintuitive bits.
Ideally, variable names should be intuitive enough that they explain themselves: for example, if you have a variable named `analysis_parameters` you know it's the parmaeters for an analysis, whereas calling it `x` doesn't tell you anything about it. 
Sometimes though you will do some clever trick that you wouldn't understand if you came back a month later, so that should be commented!

### Stage 2: Defining functions in a Jupyter notebook
If you're copying lines of code around, it's time to define a function instead.
This pushes you to make the function generic enough to fulfill multiple purposes, which is good!
There's a time and a place for making functions *maximally* generic, but for now just make them as generic as need them to be. 

In addition to cleaning up your notebook, this also helps you avoid screwups where you change some variables but forget to change others **which happens very often!**

*Mini-tip:* I am serious, like 75% of all errors will be some incorrect input value somewhere.
I personally have taped a sign saying "Always check inputs first!" to my wall because I reflexively forget about this myself!

So, don't copy, define a function and call it in each cell where you need it!

**How do I  know it's time to switch to stage 3?** *If you find yourself copying code between notebooks* then it's time to go to stage 3 and make a `.py` file. 

*Mini-tip:* You may try to avoid this by having a mammoth notebook containing 100's of cells.
The problems with this will be self explanatory when it takes 10 seconds to scroll to the bottom, but sufficed to say that keeping notebooks clean and targeted (basically, one notebook per task you are trying to complete) will help you stay sane!

*Documentation tip:* At this stage the appropriate level of documentation takes the form of docstrings, which are comment blocks just under the function definition that give the parameters, return values, and a brief explanation of the function.
See, for example [the numpy style guide](https://numpydoc.readthedocs.io/en/latest/format.html) to learn how to write these effectively.
It can also be good to typehint your code at this stage, which means annotating the function definition so that you know what types it takes and returns - this will help IDEs like vscode catch common bugs!

### Stage 3: Make a `.py` file for your functions
If you are making many notebooks to do discrete tasks (as you should!) you will find yourself doing certain tasks in all of them (for example, reading in and pre-processing data).
Here, you should simply cut and paste the functions you've been defining in stage 2 into a `.py` file (for example `myfunctions.py`), and then you can import them in each notebook (for example, `from myfunctions import *`). 
The needs of the functions will probably vary by context, which is an incentive to generalize them further!

**How do I know it's time to switch to stage 4?** *If you find yourself copying that `.py` file between projects*, it's time to make it into a python package.

### Stage 4: 

You are presumably familiar with python packages already, and use them all the time.
But the final tier of python programming is to be making those packages yourself!
Doing this does have some overhead (and I will develop a tutorial module for doing so in this repository!) but it's the best way to access your own code across circumstances, and especially share it with others!

*Documentation tip:* At this phase, you should put together a full set of document webpages, including license, tutorials, and so on. At some point I'll make a tutorial showing how to do this with `mkdocs`, which is my personal preference. 