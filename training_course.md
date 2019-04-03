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
Variables are extremely useful because they allow us to store information for later use. Variables can be anything from a number, a string, a matrix, a datatable, etc. Variables are powerful because they will stay in the global environment as long as you keep Rstudio open. Variables also can be overwritten.

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
* `x + y`

These operationals can also be used to make new variables. For example, if I wanted the sum of two things to be a new variable `z` I could run this.

`z <- 4 + 3`

Now lets say you want the sum of `z` and `x` to be `y`. Write a line of code that will create a new variable `y` that is the sum of `x` and `z`.

### Basic Functions
Functions are the backbone of using Rstudio efficiently. A function is a command that calls upon a already saved set of code that is stored by either Rstudio's base package or a new package that you installed. This will reduce the total amount of code that you would need to write and run. For example, in the last section if we wanted to sum together 1, 2, and `x`, we could input `1 + 2 + x`. However, if we wanted to be fancy and use the `sum()` function, it would look like this `sum(1,2,x)`. Go ahead and try that now. 

Some other functions you may want to play around with
* `sqrt(49)`
* `abs(-7)`
* `log10(x)`

### Creating Functions
Let's say you want to go to Europe this summer, however, Europe measures their temperature in Celcius and we measure our temperature in Fahrenheit. There is a conversion to get from fahrenheit to celsius the equation is `(F - 32)\*(5/9) = C`. So if we started at a nice 70 degree fahrenheit and wanted to get to celsius we could use our console and go
* `(70 - 32) * (5/9)`
But that's a lot of typing to find a simple conversion. So instead of having to manually type out the formula every time, we can create a function similar to `sum()` or `sqrt()` to do this quickly.

To make a function we have to first start out by naming it. Lets name out function `FtoC` (Fahrenheit to celcius). Similar to how we declared variables we can declare functions.
```
FtoC <- function(argument) {
statements
return(object)
}
```
Now we can use the `function()` function (hehe). A function contains 3 parts
1. Arguments - what is inputted, so in out example it would be the temperature in fahrenheit (`f`)
2. Statements - what happens to the arugments, in our example it would be the equation (`C = (f - 32) * (5 / 9)`)
3. A return/output - what the funtion returns, in our example it would be the temperature in celcius (`c`)

Lets add these to our code
```
FtoC <- function(f) {
c = (f - 32) * (5 / 9)
return(c)
}
```
Now to save this function to our global environment, we will have to run the whole command into the console. After that, you should see the `FtoC` function in your global environment box in the top left.

Now we can finally run that function! Go ahead and choose your favorite temperature in fahrenheit and plug it into the function. My favorite temperature is a cool 75 degrees celcius so I will run `FtoC(75)`.

Great job! You just wrote a function to change temperature from fahrenheit to celcius and tested it out and it (hopefully) worked!

Now go ahead and **write a new function** that accepts an argument of temperature in **Celcius** and **outputs fahrenheit**.

## Working with data
Today, one of the biggest challenges that researchers, companies, and other organizations face is the sheer amount of data available to them. Rstudio allows us to take large amounts of data and visualize it. For this next section, we will be working with a sample data set I created. 

### Downloading Data
The  data set is located in this github repository under the name `sample_data.csv` [here](https://github.com/prvasquez/crc_rstudio_class). Open the page in a new tab, and on the left side of the page you will see a green box that says "Clone or Download". Click that then click "download ZIP".

![alt text](https://github.com/prvasquez/crc_rstudio_class/blob/master/downloadzip.png)

After downloading the file, we will have to decompress it and move the `sample_data.csv` file to our computer. Go ahead and move the download to your Desktop. Next, unzip the folder and drag the `sample_data.csv` file to your desktop.

Once the file is on your desktop, you will have to change the working directory on the Rstudio software. To do this, click on session -> Set working directory -> Choose directory. When choosing the directory, go to the Desktop directory and open it.

You should see this command come up in your console `setwd("C:/Users/itlm094/Desktop")` as well as the `sample_data.csv` appear in the files square at the bottom right of the rstudio window.

### Opening Data files
Now that `sample_data.csv` is in our working directory, we will need a way to access the data inside it. One way to do this is by simply clicking the file and then clicking `view file`.

When you do this, a new box will open in the top left corner that looks like this.
```
Day,Temperature
Monday,30
Tuesday,32
Wednesday,28
Thursday,25
Friday,31
Saturday,332
```
A few things to notice about this file.
* **The Header** - The first line of a file is usually called a header (although not all files will have headers). This line will be important later when we start using our data.
* **The Commas** - You may have noticed the `.csv` extension at the end of our file. That stands for `Comma Separated Values`. Different types of files need to be imported into Rstudio in different ways. Another similar file type you may see is `.tsv`, which stands for `Tab Separated Values`. As you can imagine, instead of commas the values have a tab space between them.
* **Saturday is HOT!** - It seems like Saturday will be a really hot day at 332 degree celcius! Keep this in mind for later and we can fix it with our newly learned R skills!

### Opening Data files and storing them in Rstudio
When we opened the `.csv` file all we saw was how the text inside the file. But what if we wanted to ask Rstudio what the temperature was on Wednesday? There is no command that would work on the `.csv` file, so instead we will first have to import the csv file as a table into our Rstudio enviornment. There are two ways to do this.

1. Manually import the data by going `File` -> `Import Dataset` -> `From Text (Base)...` then select the `sample_data.csv` file and click open then import! 
2. In your console, you can use the `read.csv()` function. Let's run through this function's variables so we know what were doing.
```
read.csv(file, header = TRUE, sep = ",")
```
* `File` The file you want to read from.
* `header = TRUE` If you file has a header, then you can leave this variable as `TRUE`, however, if the file does not have a header then switch to `FALSE`
* `sep = ","` What to look for to separate the data. If you remember from when we viewed the text file, our data was separated by commas! (Also `.csv` stands for **Comma** separated values). If, however, our data was in the **tab** separated values. We would put `sep = \t`.



Now your data is saved as a dataframe in Rstudio

