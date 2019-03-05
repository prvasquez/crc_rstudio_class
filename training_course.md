# Welcome to the Spring 2019 Rstudio Training course!
This course will serve to provide an informational session about Rstudio and its applications.
By the end of this course you will hopefully...
* Become more familiar with the Rstudio software
* Become more familiar with the programming language R
* Be able to wirte and run simple code in Rstudio

## Rstudio vs R
Rstudio is a **GUI** (Graphical User Interface). This software allow the us to easily visualize the information we are working with.

R is a **programming language**. Whenever we run code, we will be using the language R.

## Opening Rstudio
Go ahead and open the Rstudio application.

After opening go to File > New File > R Script (Keyboard shortcut is Ctrl+shift+N). This will open an additional box in the top left corner of your Rstudio screen.

![alt text](https://github.com/prvasquez/crc_rstudio_class/blob/master/rstudio.png)

1. Your R script that you are making. This box can serve multiple purposes, one can be to copy and paste the commands you wrote so that you don't forget them.
2. Your global environment. This box will show the data that is currently stored in your Rstudio session, an example would be a global variable.
3. Your command console. This is where you can write in code to run. You will use this a lot.
4. Files, plots, packages, etc. This is the miscellaneous box. It has a little bit of everything but we won't worry bout it too much today.

## Using the Rstudio Console
The console is the central location that you will enter your code. Go ahead and try to enter random stuff into the console. Here a short list of things to try.
* A number `4`
* A word `hello`
* A word that has quote around it `"hello"`

**What worked? What didn't work? Why?**

### Types of data
From the previous section you'll notice that typing in certain values and characters has the chance to return an error.
* `4` returns `4`
* `"hi"` returns `"hi"`
* `hello` returns `Error: object 'hello' not found`
R can recognize numbers, data tables, matrix, and strings/characters. `4` is a number so it worked. `"Hello"` is a string (because it has the quotes surrounding it) so it worked. But `hello` by itself is a variable.

### Variables
Variables are extremely useful because they allow us to store information for later use. Variables can be anything from a number, a string, a matrix, a datatable, etc.

Let's store our first variable! Go ahead and plug this command in the console.
`x <- 5`
You should notice one thing right away, in the top left box you should see a new heading called "values" and under that you should see `x` next to the number 5.

Now go ahead and plug `x` into the console. What do you think it will return?

### Basic Operationals
In addition (*pun intended*), you can do basic mathmatical operations in Rstudio such as addition, subtraction, multiplication, and division. Let's start with some easy math. Go ahead and see if you can guess what Rstudio will output for these codes. After guessing, go ahead and type it into the console and see if you're right!
* `1+1`
* `2 - 7`
* `84 / 12`
* `2 * 3`
* `2 ** 3`
* `2 ^ 3`
* `4 + 7 * 3 ^ 2` *Hint: Order of operations still applies*
* `x + x`
