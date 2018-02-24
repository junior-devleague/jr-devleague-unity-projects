# Variables and Data Types

## Variables

### Comments

#### `//`

Before we go into Variables, it's important to first understand how Variables are declared and the syntax (format) of how it's formed.  Generally, Variables have a very strict declaration on how it wants to be created.  

* The first and generally very important concept to learn are called "Comments".  
* Comments are created by using **two slahes** or `//`, comments are useful for leaving notes for yourself or for other people who are reading your code.  
* Anything written inside of the comments will be ignored by your IDE. 
* It's usually a good idea to leave very intricate notes that can help detail what a function is used for or what a variable is meant to contain.   

### Variables and Variable Declaration

A variable is an empty container.  It is simply a empty box with a name on it that is used to hold data for us.  Our data goes into the box and is stored for us to use whenever we need it.    

As said before, variable declaration syntax is important and as such should be treated carefully.  Mistakes made in variables can cause a huge mess of compiler errors.

A Variable declaration goes as so: `Type of Access, Type of Variable, Name of Variable, Value of Variable`

or `public int myInt = 5;`

#### Type of Access: `public or private` 

* Public - Public means that a script is able to be accessed from outside of the script it was created from.  Public variables means you can put data from your project directly into the variable to be held and manipulated.  Variables are able to hold any type of data including value for the correct data type or even GameObjects.  With a Vector3 for example, you are even able to hold multiple value types including data points for an x,y, and z coordinate.   

* Private - A Private variable means that it is not able to manipulated or accessed from outside of the script.  That means values can't be changed unless it is directly altered from the script.  

#### Type of Variables

There are 4 different types of Primitive Data Types that are able to be used.  Notice these are primitive because they are considered default data types used in C#.  These four are:

* `int` - A type of data type meant primarily for numbers.  Int's should primarily be used for whole numbers.  Decimal points are NOT recommended for int's. The difference between `int` and `float` is that C# and Unity will convert int types into float values which are primarily used for functions.

`public int myInt = 10;`

* `float` - As mentioned earlier, `float` values are the primary number data type used for functions.  In general, there isn't a difference between int's and floats except for the fact that floats ARE ALLOWED to have decimal places.

`public float myFloat = 10.53`

* `string` - A string represents text which to us, forms sentences. To a computer, however, it is simply an arranged order or characters.  To define text, you would put your text in between quotation marks. Like so:

Strings are strictly meant *only* for text, so applying numbers to a string data type -and vice versa- will give you a compiler error or it won't even work in the first place.  

`public string myText = "Wow, this is my line of text!"`

* `boolean` - A boolean is a data type that only holds two acceptable types of data.  `true` or `false`, both of these are **keywords** or placeholders which Unity already recognizes and has a definition.  Things like checkmarks in Unity are simply boolean values.  A boolean variable with a value of `true` will have a checkmark, while boolean data types with a `false` value will be unchecked.

#### Name of variables

* As with any other variable in programming, variables need to have a declared namespace for reference.  
* A variable will have a name that will describe what the variable is being used for.  
* Names for variables are allowed to be numbers and even special characters as well. 
* The **only** character that is not allowed to be used is the `_`.  
* Remember that `CamelCase` is **VERY** important and should be used in ALL cases.  I.E. `myIntegerIsTheBestIntegerInTheWorld`

## If you have read through and have a understanding of variables and Data Types, ask about the Quiz on Values and Data Types!
