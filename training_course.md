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

### For loops

What would happen if you needed to run your temperature conversion function on 100 different temperature values? Well you could 1) type out each value into the function like so.
```
FtoC(1)
FtoC(2)
FtoC(3)
FtoC(4)
# and so on
```
**Or** you could iterate through all the numbers with one command! A **For loop**. Lets go over the basic structure of a for loop.

```
for (i in x){
        statement
}
```
**X** is a range of numbers or how many times you want to do the looping and what `i` will be equal to. For example, if you wanted to iterate through the numbers 1 through 10, you could do `for (i in c(1,2,3,4,5,6,7,8,9,10))`. But that seems like a lot of work if you wanted to do 1 through 100... so R has a built in function to make this easy, the colon `:`. So if you want to say 1 through 10 you would do `1:10` and if you wanted to do 5 through 15 you would do `5:15`.

**Statement** the statement portion of the for loop is what you want to do on every iteration, it must include the `i`.

### Practice with For loops

One useful function is the `sum()` command, which sums the numbers inside of it. So, `sum(1,2)` would equal 3(You can try this if you would like). However, lets say you forgot how to use the `sum()` command! This is an example of a for loop that you could run to take the sum of the numbers 1 through 100.

```
total = 0 # Start by assigning the total to 0
for(i in 1:100){ #iterate i from 1 to 100
        total = total + i # add i to the total
}
print(total) # print out the total
```





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
read.csv(file, header = TRUE, sep = ",", stringsAsFactors = )
```
* `File` The file you want to read from.
* `header = TRUE` If you file has a header, then you can leave this variable as `TRUE`, however, if the file does not have a header then switch to `FALSE`
* `sep = ","` What to look for to separate the data. If you remember from when we viewed the text file, our data was separated by commas! (Also `.csv` stands for **Comma** separated values). If, however, our data was in the **tab** separated values format. We would put `sep = \t`.
* `stringsAsFactors = ` This variable looks for either a `TRUE` or a `FALSE`. Don't worry about this one for now, we will discuss it later.

`data <- read.csv("sample_data.csv", stringsAsFactors = FALSE)`

Now your data is saved as a dataframe in Rstudio called `data`. You can view the data as a table with the `View()` command. You should see a data table that looks like this.

![alt text](https://github.com/prvasquez/crc_rstudio_class/blob/master/datatable.png)

### Checking data blocks

Now that we have our data set up, we need to learn how to use R commands to access it.

The most simple command is just typing in `data` into the console. Go ahead and try that. The console should return the data table but printed out. You can see there are 6 rows, each representing a day, and 2 coloumns, one for "day" and one for "temperature". You can also use `View(data)` which will bring up the table in the top left. **Note: The `View()` command has a capital V**

#### Check the names of columns

If you want to check what the names of columns are use the `colnames()` function.
```
colnames(data)
[1] "Day"         "Temperature"
```

What if we wanted to see what the data was in a column? For that, we would have to call certain parts of our dataframe. The syntax for that is `data[row,column]`. However, if we just want to see what a column looks like we can just use `data[column_number]`.

So to check the data in column 1...
```
> data[1]
        Day
1    Monday
2   Tuesday
3 Wednesday
4  Thursday
5    Friday
6  Saturday
```
And then column 2...
```
> data[2]
  Temperature
1          30
2          32
3          28
4          25
5          31
6         332
```

### Change the wrong data block

Now that you know the syntax, you should be able to call certain boxes from the matrix. `data[1,1]` should give us the data in row 1 column 1 (which is Monday).

```
> data[1,1]
[1] Monday
6 Levels: Friday Monday ... Wednesday
```
How about `data[2,2]`?
```
> data[2,2]
[1] 32
```

If you remember back to when we were checking out the dataset, we saw that Saturday's forcast was supposed to be 332 degrees! That is HOT! We need to change it down to something reasonable. To do that, first we have to find which command calls the table spot where we have the incorrect data.

Go ahead and find what that command is.

Once you have the command, go ahead and asign that block a new value that you think is what the temperature will be. To do that, you will have to run the command like this.
```
#command <- #temperature_you_want_to_input
data[6,2] <- 32
```

Good job! Now Saturday won't be as hot! Now lets add some data in, add to the table so that there is a new day `Sunday` and make sunday be a cool `25` degrees. We can do that manually by assigning values to two new data boxes in the 7th row.

```
# For the day
data[7,1] <- "Sunday"

# For the temperature
data[7,2] <- 25
```

Easy-peasy! But now imagine a data table that has thousands of boxes! Doing this one-by-one would take a very long time and have a high rate of error. We will learn how to add whole new rows/columns later on.

### Operations on data(mean avg etc)

Lets say we want to find out what the average temperature will be across our whole dataset. One way we could do that is open the calulator app on our phone, go down the list adding up all the temperatures, and then divide by how many rows we added. Now imagine a dataset with 1000+ rows... that might get a bit tidious. Thankfully, Rstudio was designed to handle large datasets and the base package comes prepared with a whole suite of mathmatical functions we can perform.

One thing to keep in mind is that when performing functions, we can only perform them on **numeric** objects. So we would not be able to ask what the mean of `Monday + Tuesday + Wednesday...` is but instead we have to ask what the mean of `30 + 32 + 28 + 25...` is. The function for `mean()` is as follows.
```
mean(x)
```
Where x is a vector of numbers. But how do we get a vector of numbers from out dataset? Well we know that we need the `Temperature` column from our dataset `data`. To call specific columns of a dataset the syntax is `dataset$(name_of_column)`. So if we wanted to see all the days in the day column we would run the command...
```
> data$Day
[1] "Monday"    "Tuesday"  
[3] "Wednesday" "Thursday" 
[5] "Friday"    "Saturday" 
[7] "Sunday"
```

So now that you know what the function for mean is and you know how to call columns from a dataset, go ahead and **find what the mean temperature will be.**

### Adding a new column, w/ temperature function from before

Now we are going to bring everything together and add a new column onto our data table that is the temperature in Fahrenheit!

* **HINT** Use a For Loop!

## Packages

The base language of R is expansive and has a lot of tools. However, R by itself cannot do everything you could want! In response to that, developers can independently make add-ons or **PACKAGES** which complement the language and allow the user to do more things! For example, the base R package has a `plot` command. However, it only makes a very simple graph. Go ahead and try.
```
plot(data$Temperature)
```
But what if we wanted to make box plots or other types of advanced plots... well we would have to use a package!

### installing, loading, etc

There are some packages that are already installed that come with Rstudio! To checkout these packages, click the `packages` option in the bottom right box of Rstudio. You can scroll through and check them out (there's a lot)! Because these packages are already *installed* all we have to do is **Load** them.

Lets go ahead and load the `maps` package. You can do that by calling the `library()` function.

```
library(maps)
```
Now that we have the maps library loaded, lets call it and see what we can do with this package!
```
map('county','indiana', fill = TRUE, col = palette())
```
If you want to see whatelse you can do with a package, you can checkout the documentation by adding a `?` before the name of the library like so `?map`

### What types of packages (bioconductor)
In addition to the many packages that already come with R, there are many on the internet that you can download and use for yourself.


## Plotting
### different types of plotting

## Data sets
### Do something with a new data set
