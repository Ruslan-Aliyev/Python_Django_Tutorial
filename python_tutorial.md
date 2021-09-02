# Python Tutorial

https://www.youtube.com/playlist?list=PLsyeobzWxl7poL9JTVyndKe62ieoN-MZ3

## Setup

### Ubuntu

- http://ubuntuhandbook.org/index.php/2017/07/install-python-3-6-1-in-ubuntu-16-04-lts/

### Mac

Python: https://www.python.org/downloads/ Download the `.pkg` and run the wizard.

Or via Brew: https://docs.python-guide.org/starting/install3/osx/

In my case, I already found Python 2 which came with my Mac `/System/Library/Frameworks/Python.framework`.  
I also found Python 3 in `/usr/local/Cellar/python@3.9` (Which I probably installed earlier).  
I can already use `python` and `python3` in my terminal, so no need to add them to path.
But I can't yet use `pip` in my terminal.
I also found that the default `python --version` is Python 2.

So I did below:

```
touch ~/.profile
open ~/.profile
```

```
alias python='python3'
```

`open ~/.bash_profile`

```
source ~/.profile
export PATH=/usr/local/Cellar/python@3.9/3.9.5/bin:$PATH
```

`source ~/.bash_profile`

### Windows

1. Download and install Python and PIP https://www.python.org/downloads/. 
	- Put Python and PIP into PATH 
		- https://www.youtube.com/watch?v=4V14G5_CNGg&list=PLsyeobzWxl7poL9JTVyndKe62ieoN-MZ3&index=9
		- ![](/Illustrations/python/python3_win10_paths.PNG) 
	- Check with `python --version` & `pip --version`. 
2. Setup a **virtual environment** . Having a virtual environment means that Django configs won't be computer-wide, but per-project.
	- `venv` is a package that comes with Python 3. Python 2 does not contain `venv`.
		- `python3 -m venv test`
		- `source test/bin/activate` or `test\Scripts\activate` for Windows
	- `virtualenv` is a tool that allows you to create isolated Python environments, which can be quite helpful when you have different projects with differing requirements. It is a library that offers more functionality than `venv`. ( https://help.dreamhost.com/hc/en-us/articles/115000695551-Installing-and-using-virtualenv-with-Python-3 )
		- `pip3 install virtualenv`
		- `virtualenv -p python3 test`
		- `source test/bin/activate`
	- mkvirtualenv is command under virtualenvwrapper which is just a wrapper utility around virtualenv that makes it even easier to work with. ( https://stackoverflow.com/questions/44063274/differences-between-mkvirtualenv-and-virtualenv-for-creating-virtual-environment )
		- `pip install virtualenvwrapper-win  # create the env wrapper`
		- `mkvirtualenv test                  # create the env`
	- Navigating virtual environments
		- https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/26/python-virtual-env/
		- https://stackoverflow.com/questions/990754/how-to-leave-exit-deactivate-a-python-virtualenv
			- If you exited an virtual env and want to re-enter: `workon test`
		- `lsvirtualenv` to list all virtual environments.
	- In my example, I used `virtualenvwrapper-win` and then created a virtual environment called 'test'

## Uninstall

### Ubuntu

### Mac

- https://stackoverflow.com/questions/3819449/how-to-uninstall-python-2-7-on-a-mac-os-x-10-6-4
- https://www.macupdate.com/app/mac/5880/python/uninstall

### Windows

## Manage Versions

### Ubuntu

### Mac

- Python: https://stackoverflow.com/questions/18425379/how-to-set-pythons-default-version-to-3-x-on-os-x
- Upgrade PIP: `/usr/local/opt/python@3.9/bin/python3.9 -m pip install --upgrade pip`

### Windows

## IDE

### Ubuntu

- PyCharm: 
	- https://itsfoss.com/install-pycharm-ubuntu/
	- https://www.cs.rit.edu/~csci141/Docs/PyCharm-Setup.html
	- https://stackoverflow.com/questions/55749206/modulenotfounderror-no-module-named-distutils-core

### Mac

- PyCharm: https://www.jetbrains.com/pycharm/download/ Drag `.dmg` into `~/Applications/`.
- Jupyter Notebook: https://jupyter.org/install 
	```
	pip install notebook
	jupyter notebook
	```

### Windows

- PyCharm: https://www.youtube.com/watch?v=akcEaEH91gI&list=PLsyeobzWxl7poL9JTVyndKe62ieoN-MZ3&index=20
- SublimeText: https://www.youtube.com/watch?v=1U8TI16AR4s&list=PLsyeobzWxl7poL9JTVyndKe62ieoN-MZ3&index=11&t=145s

## Features

IDLE - for using Python in terminal

Pygame - Modules for video games.

wxPython - a wrapper for the cross-platform GUI API (often referred to as a "toolkit") wxWidgets (which is written in C++) for Python. 
It is one of the alternatives to Tkinter. It is implemented as a Python extension module (native code).

SciPy - a computing environment and open source ecosystem of software for the Python programming language used by scientists, analysts and engineers doing scientific computing and technical computing. 

QGIS (Quantum GIS) - a cross-platform free and open source desktop GIS application

IPython includes an architecture for interactive widgets that tie together Python code running in the kernel and JavaScript/HTML/CSS running in the browser. 

DIS library shows Python bytecode

Pandas - a software library written for Python for data manipulation and analysis. In particular, it offers data structures and operations for manipulating numerical tables and time series.

Graphite1 - Python library: storing numbers that change over time and graphing them.

Python Package Manager (PyPM) - a Python utility intended to simplify the tasks of locating, installing, upgrading and removing Python packages.
PyPM uses PyPM Repositories (collections of pre-compiled packages). 
These repositories contain a high variety of modules, published on PyPI.
PyPM is inspired by Perl package manager (PPM).

PIP - a package management system used to install and manage software packages written in Python. Many packages can be found in PyPI.

Conda - a cross-platform, Python-agnostic binary package manager. It is the package manager used by Anaconda installations.

Anaconda - a free collection of powerful packages for Python that enables large-scale data management, analysis, and visualization for Business Intelligence, Scientific Analysis, Engineering, Machine Learning

Binstar - a service that allows you to create and manage public and private conda packages in multiple channels.

## Variable Types

![](/Illustrations/python/var_types.PNG)

- There is also `null`
- Numeric can be
	- int
	- float
	- complex
	- bool

**Important**: Python doesn't pass by value nor by reference. It passes by object-reference:
![](/Illustrations/python/obj_ref_1.PNG)
- variable -> "box (a reference to object)" -> object
- https://robertheaton.com/2014/02/09/pythons-pass-by-object-reference-as-explained-by-philip-k-dick/
![](/Illustrations/python/obj_ref_2.PNG)
- 10 is an object.
- Object is like a box where data is held.
- Every object have an ID (memory address).
- If 2 variables have the same data, they will point to the same box.
- Address is not based on variable, but based on box.

### Strings

- Concat using `+`
- `_` represents the previous result
- Strings in Python are a sequence of chars, so you can access the char(s) by `string_variable_name[i]` or `string_variable_name[i:j]`
- Strings are immutable, so you can't do `string_variable_name[i] = 'x'`
- Get string length: `len(string_variable_name)`

### Lists like structures

https://data-flair.training/blogs/python-data-structures-tutorial

- **List**: Mutable, diff types elements `[]`
	- https://www.w3schools.com/python/python_lists.asp
		- Methods: https://www.w3schools.com/python/python_lists_methods.asp
			- Also: `max(list_variable_name)`, `min(list_variable_name)`, `sum(list_variable_name)`
	- `del list_variable_name[i:j]` deletes a portion of the list elememts
- **Tuple**: Immutable list `()`
	- https://www.w3schools.com/python/python_tuples.asp
- **Set**: Unordered (Set uses a hash concept to fetch elements as fast as possible), unindexable list, unique elements `{}`
	- https://www.w3schools.com/python/python_sets.asp
	- **Dict**: `{1: 2, 2: 4, 3: 6}`
		- Methods: https://www.w3schools.com/python/python_ref_dictionary.asp

#### Zipping Tuples

![](/Illustrations/python/zip.PNG)

### Plain Python Arrays

Same element type list, must declare type. expandable.

```
from array import *

vals = array('i', [1, 2, 3])

for item in vals:
    print(item)
```

![](/Illustrations/python/array_element_types.PNG)

### NumPy Arrays

NumPy - a library giving support for large, multi-dimensional arrays and matrices & high-level math functions to operate on these arrays.

- https://www.datacamp.com/community/tutorials/python-numpy-tutorial
- https://www.datasciencelearner.com/how-to-install-numpy-in-pycharm

![](/Illustrations/python/numpy.PNG)

Make multi-dimensional, different-element-type array by using NumPy:
```
from numpy import *

vals = array([5, 6, 'oo'])

for item in vals:
    print(item)
```

![](/Illustrations/python/create_numpy_arrays-various_ways.PNG)

#### Adding NumPy Arrays

https://www.educative.io/edpresso/how-to-add-one-array-to-another-array-in-python

## Modules

### Using modules, eg: `math`

- `from math import sqrt, pow`
- https://www.w3schools.com/python/module_math.asp

### Making customer modules

![](/Illustrations/python/modules.PNG)

## User input

![](/Illustrations/python/input.PNG)

## kwargs

![](/Illustrations/python/named_arguments.PNG)

https://treyhunner.com/2018/04/keyword-arguments-in-python/

## `sys.argv`

https://www.pythonforbeginners.com/system/python-sys-argv

## Anonymous Functions aka Lambda

![](/Illustrations/python/lambda.PNG)

## Filter Map Reduce

![](/Illustrations/python/filter_map_reduce.PNG)

## Special Variables & Methods

- http://exampleprogramming.com/specialvars.html
	- https://www.geeksforgeeks.org/__name__-special-variable-python/
- https://dbader.org/blog/python-dunder-methods

## Operators

- https://www.w3schools.com/python/python_operators.asp
- https://jakevdp.github.io/WhirlwindTourOfPython/04-semantics-operators.html

## Operator Overloading

Operators like `+` are actually dunder/magic methods (`__add__`) under the hood.

To alter `+`'s behaviour, just define it again with your own logic:

```py
def __add__(self, other):
	# custom logic
	# return ...
```

- https://www.programiz.com/python-programming/operator-overloading

## Decorators

Alter behaviour of existing operators/functions

![](/Illustrations/python/decorators.PNG)

## OOP, Variable & Method Types

![](/Illustrations/python/statics.PNG)

## OOP, Abstract

![](/Illustrations/python/abstract.PNG)

## Duck Typing

If an object is of a parent class type and have certain method(s), then it will be accepted.

![](/Illustrations/python/duck_typing.PNG)

## Iterators

![](/Illustrations/python/iterator.PNG)

### Custom Iterators

![](/Illustrations/python/custom_iterator.PNG)

## Generators

Generators give Iterators

![](/Illustrations/python/generators.PNG)

## Exceptions

![](/Illustrations/python/exceptions.PNG)

## Threads

![](/Illustrations/python/threads.PNG)

## File handling

- https://cmdlinetips.com/2011/08/three-ways-to-read-a-text-file-line-by-line-in-python/

## DB

![](/Illustrations/python/db.PNG)

## Socket Programming

https://www.geeksforgeeks.org/socket-programming-python/
