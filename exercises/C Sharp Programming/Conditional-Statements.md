# Conditional Statements and Logical Operators

## Conditional Operators

Conditional Operators are simply symbols that we use inside of our scripts to compare two things.

The different Conditional Operators we have are:

`=` - Data or value is equal

`===` - Data *and* Value is equal

`>`- Left is Greater Than Right

`<`- Right is greater than left

`>=` - left is greater than or equal to right

`<=` - right is greater than or equal to left

`!=` - left value is NOT equal to right

`!===` - left value and data type is NOT equal to right

A condition will either be true or false, depending on the statement and the values.

For example, say we have:

var x = 10;

and 

var y = 5;

If we say, x > y, it will be `true` and C# will consider it so.

If we say x === y, however, this will NOT be true and will be considered 'false' to Unity.  This will be useful for our next subject which are called **Conditional Statements**.

## If, else, else if 

Imagine you're at a Supermarket and you find yourself in the liquor section.  You need to be at least 21 to be able to purchase alcohol,  let's simulate a situation where Jimmy wants to double check his age to make sure he's 21 using our new Conditional Operators.

The point of a Conditional Statement is to put a clear requirement on our script to run something ONLY if something else is true (or false).

The first conditional statement we're going to discuss is an "if" statement and it looks like this:


 if(*requirement goes here*) {

    run(execute) this block of code

  } 
  
If the requirement is true, the code in between the braces will activate.  If it is false, the block of code will be ignored.

Firstly, in the C# Programming Project, create a new script called ConditionalStatements.cs

Inside, first start with creating a public int age.  We don't have to give it a value just yet, we can apply a value later on.  This called a variable "declaration".  We're reserving the name "age" for an int variable and the project will remember it for us.  

Now, in the situation, the cashier is either going to give us a heads up or a heads down to whether we can buy the alcohol or not.  This is equivalent to being either "true" or "false".  

*Unlike other languages you may have learned, you are **NOT** allowed to put a conditional statement inside of a class.  Classes are only allowed to have variables, or functions.  So in this case, to use the conditional statement, we will have to put it inside of a function.*  

We're going to put the conditional statement inside of our start function.

Inside of our Start fucntion, start by first saying "if" and then parenthesis.  Inside of our parenthesis is where we put our requirement, or (if age >= 21) In this case, if we are 21 we can still buy alcohol so we can use `>=` or greater than or equal to.

It should look like:

void Start () {
  if(age >=21){
  
  }
}

Then, inside of the inside braces, we can use a simple Debug.Log to tell us "Jimmy can purchase the alcohol! Party time!"

Then, when we hit play on our scene, we will get a debug.log if Jimmy is over 21!

Now, we are going to learn about an "else" statement.  "else" statements Go at the end of an "if" statement and it basically means **"Run this if the if statement doesn't run"**

So, let's say Jimmy isn't 21 yet.  We can create an if/else statement to continue our last Conditional Statement.

It would look like this:

void Start () {
  if(age >=21){
  
  } else {
  run(execute) block of code
  }
}

Go ahead and put the change in yourself.
