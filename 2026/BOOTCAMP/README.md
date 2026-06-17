# 2026 Python Bootcamp

This part of the repository provides worksheets and support videos to guide you through some basic content you will need to know to engage with the computational neuroscience course. 

Please start working on the materials in advance, following the indications shared with you over email and whatsapp. 

We ask you to choose and complete an exercise (see **"[Exercises](https://github.com/comptelab/BIORTC_Nigeria/blob/main/2026/BOOTCAMP/README.md#exercises)"** below) ahead of the Bootcamp, to help us get an idea of everyone's coding knowledge. 


## Before we start: setting up

There are different options to run code: _locally_ or using _cloud computing_. You can use different things at different times, depending on the purpose of the code, or how good the internet connection is. 

- To run things _locally_ on your computer, you can start by installing:
  -  the [Anaconda package](https://www.anaconda.com/products/distribution), which comes with everything we need for the class;
  -   [Python](https://www.python.org/downloads/); 
  -   an IDE (Integrated Development Environment), which is where you will write your code. We recommend [VSCode](https://code.visualstudio.com/Download).  
  
- The easiest option for running Python codes is in the _cloud_, using Google Colab, which is a free service. Just click on the "Google Colab" icon next to an assignment to open it in Google Colab (you can also go to the [Google Colab homepage](https://colab.research.google.com/) and import a notebook from your computer or with an url. 


## Essential knowledge: linear algebra, calculus, statistics
A basic understanding of linear algebra is not only useful to code efficiently, it is essential for the successful completion of this course (and for making sense of advances in computational neuroscience). 

If you are already familiar with the core concepts (**vectors, matrices, linear transformations, eigenvectors and eigenvalues**), feel free to move onto the next section. Otherwise, please work through [3Blue1Brown's linear algebra crash course](https://www.3blue1brown.com/topics/linear-algebra), which is a really good resource to build some intuition. 

Also extremely useful is their [calculus crash course](https://www.3blue1brown.com/topics/calculus).

Finally, we also ask you to refresh your knowledge of basic statistics. The [tutorial videos](https://compneuro.neuromatch.io/tutorials/W0D5_Statistics/chapter_title.html) covering prerequisite training for the Neuromatch online course are a great resource for this. 


## Basics of Python coding and algorithms
The word _algorithm_ might seem a bit scary if you are new to coding, but in reality it's just a set of instructions. In this first part of the bootcamp we will work on building some intuition of how Python and algorithms work. 

**Karel the Robot** is a simple virtual robot created by Richard E. Pattis in 1981, designed to teach fundamental programming concepts.  

![Karel World](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcompedu.stanford.edu%2Fkarel-reader%2Fdocs%2Fimages%2Fch1%2Fworld.png&f=1&nofb=1&ipt=a96c726da6bc255557da4be0c6e10b348dcc8c5ad52a2222129f9ddd1f292365 "Karel World")

- **World**  
  A 2D grid of “streets” (rows) and “avenues” (columns), with optional walls and beepers (the diamond shaped objects) placed at grid intersections.  
- **Commands**  
  Karel only has 4 commands, and in the various exercises you will learn how to use them to get it to do complex things.   

  - `move()` – advance one cell forward  
  - `turn_left()` – rotate 90° counter-clockwise  
  - `pick_beeper()` / `put_beeper()` – interact with beepers  

In this part you will learn how write small programs that navigate Karel through mazes, manipulate beepers, and solve well-defined puzzles.  Head over to 
[Karel reader](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter1.html) to learn more about Karel and prepare for the first lab, and then [click here to see the challenge](https://github.com/comptelab/BIORTC_Nigeria/blob/main/2025/BOOTCAMP/Level%201%20-%20Algorithms/Lab_day1.ipynb)! 

### Exercises
After completing the Karel training and challenge, please choose and complete one of these [exercises](https://github.com/dragos-gruia/MSc-Neuroscience-Python-Course-Development/blob/main/Exercises/Exercises.md) (kindly shared by Dragos Gruia and Valentina Giunchiglia at Imperial College) and send it to the Bootcamp leader Muhammad Baba Goni `(<muhammadgoni51@gmail.com>)` by Friday 12th June at the latest. This will help us work out everyone's starting level of coding and serve as a starting point for discussions at the Bootcamp. 


## Further reading on Python coding
This section provides more in-depth materials, mostly taken from the <a href="https://github.com/SussexPAL/PythonCrashCourse">University of Sussex PAL resources</a>, to use if you want to go further. These materials will give you another run through the principles explored in the previous section, with videos and worksheets. You can also jump to the next section if you wish. 

#### <a href="https://github.com/SussexPAL/PythonCrashCourse#task-2---maths-through-programming">Maths through programming</a>

<a href="https://github.com/SussexPAL/PythonCrashCourse/blob/main/Worksheets/day_1_maths_through_programming.ipynb">Click here to view worksheet</a>

#### <a href="https://github.com/SussexPAL/PythonCrashCourse#task-3---data-types">Data types</a>
Understanding your data is key to making a program that uses it. This worksheet teaches you how to make different variables for different data, and how this is used.
* recapping bools vs numbers
* int vs float
* strings 
* lists 
* dictionaries

<a href="https://github.com/SussexPAL/PythonCrashCourse/blob/main/Worksheets/day_1_data_types.ipynb">Click here to view worksheet</a>

#### <a href="https://github.com/SussexPAL/PythonCrashCourse#task-1---statementsexpressionslogic">Statements/expressions/logic</a>
Computers use logic, 1 for on or 0 for off. Binary, at the simplest level, is a computer language. This still holds true in coding. We have True (1) and False (0) when making choices. 

<a href="https://github.com/SussexPAL/PythonCrashCourse/blob/main/Worksheets/day_2_logic_expressions.ipynb">Click here to view worksheet</a>

#### <a href="https://github.com/SussexPAL/PythonCrashCourse#task-2---flow-of-control">Flow of control</a>
* introducing scope
* loop/iterator variables
  
<a href="https://github.com/SussexPAL/PythonCrashCourse/blob/main/Worksheets/day_2_flow_of_control.ipynb">Click here to view worksheet</a>

#### <a href="https://github.com/SussexPAL/PythonCrashCourse#task-3---functions">Functions</a>
What if we want to execute the same bit of code multiple times throughout different parts of our program. Copying and pasting it will look messy, instead we can write it once as a function and recall it whenever we need it.
* simple functions
* parameters
* return values
* default parameters

<a href="https://github.com/SussexPAL/PythonCrashCourse/blob/main/Worksheets/day_2_functions.ipynb">Click here to view worksheet</a>

#### <a href="https://github.com/SussexPAL/PythonCrashCourse#task-4---understanding-errors--the-call-stack">Understanding errors & the call stack</a>
What does an error actually mean? The way that we can understand when our code breaks is understanding the error itself!
* syntax error
* overflow/timeout error
* logic error
* try catch

<a href="https://github.com/SussexPAL/PythonCrashCourse/blob/main/Worksheets/day_2_understanding_errors.ipynb">Click here to view worksheet</a>


## Applying Python to neuroscience pipelines: data processing and visualization
Being able to import and preprocess various types of data forms the foundation for all the modeling and analysis we will do in the course. In this last section, we will learn how to handle data in Python code with _numpy_, inspect and load it with _pandas_, and visualise it with _matplotlib_. This will give you all the necessary tools for working with your own datasets in your projects. Please feel free to ask questions about this section at the Bootcamp in preparation for the course. 

#### Handling of your data with Numpy
First, we will learn how to use the library _numpy_ to handle and understand scientific data in python.

<a href="https://github.com/comptelab/BIORTC_Nigeria/blob/main/2025/BOOTCAMP/Level 3 - Data Science/3a_numpy.ipynb">Click here to view the Numpy worksheet</a>

#### Using Pandas to load and inspect datasets
Next, we will learn how to load in different types of data, inspect it to understand the basic needed preprocessing steps, and then do the preprocessing. For this, we will use the _pandas_ library.

<a href="https://github.com/comptelab/BIORTC_Nigeria/blob/main/2025/BOOTCAMP/Level 3 - Data Science/3b_pandas.ipynb">Click here to view the Pandas worksheet</a>

#### Using Matplotlib to visualise your data
Last, we learn how to handle a more specifically neuroscientific dataset and visualise it with _Matplotlib_, another very useful and important library:

<a href="https://github.com/comptelab/BIORTC_Nigeria/blob/main/2025/BOOTCAMP/Level 3 - Data Science/3c_datasets.ipynb">Click here to view the Matplotlib worksheet</a>


## Further steps and challenges
If you feel comfortable with Python already and would like to do some extra reading on data analysis for neuroscience in preparation for the course, take a look at the interesting stuff on this page <a href="https://github.com/wimmerlab/MBC_data_analysis/tree/main">tutorial on Python for neuroscience</a>.

The [prerequisite online training for the Neuromatch computational neuroscience course](https://compneuro.neuromatch.io/prereqs/ComputationalNeuroscience.html) is excellent and includes general background materials on programming and maths skills.
