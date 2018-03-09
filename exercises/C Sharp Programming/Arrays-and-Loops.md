# Arrays and Loops

This guide is going to give you an understanding of Arrays and For-Loops.  Arrays and Loops work interchangeably so it is a good idea to know what Arrays are first before going into Loops.

## What are Arrays?

First thing, arrays are NOT a data type to C# Unity.
Arrays are simply a very valuable way to store multiple values in one variable.  

An array looks something like this: 

`int[] myIntArray = new int[5]` 

Now, this may looks a little confusing but don't worry we'll go over it.

The above example is creating a new array that we intend to use to store 5 integer values inside.  

We start by declaring another variable with it's **type**, however, we will put a set of brackets `[]` after the variable type.

Next we will add the name of the array, make sure to always keep it relative to what it is!

`type[] nameOfArray`

Next, we will set it equal to something.

To specify the length of the array we first start off with the new keyword, then the type of data being stored, and lastly a set of brackets with the specific amount of data being put inside of it like `[5]`.

We can then declare the index values in the ***start*** function like so:

    void start(){

    `myIntArray[0] = 12;`
    `myIntArray[1] = 76;`
    `myIntArray[2] = 8;`
    `myIntArray[3] = 706;`
    `myIntArray[4] = 950;`
    
    }
    
However, there is an easier way to declare an array.  So easy in fact, we can put it on one line. 

It looks like:

`int[] myIntArray = new int {12, 76, 8, 706, 950}`

This way is much simpler and allows us to access array the same as above.  The amount of index values being specified is also determined by the amount of values inside of the array upon declaration.

Remember that arrays index values start from 0 and not 1!

## Applying Arrays
    
We are also allowed to create arrays public so that we can access it inside of the inspector.

- Declare a new public array for GameObjects called gameObj without putting any values into it.

- Create 5 different GameObjects inside of your scene.  

- Set each GameObject's tag to "Player" this will be important for later on.

- Inside of the inspector, you'll notice there is a value called `size` this is where we can declare how many values to put inside of the array.

- By putting in `1` to size, a placeholder comes up where we can store our value inside.  In this case, we would put one of our GameObjects into it.  

- However, Unity has developed a way for us to initalize a new array easily inside of our script.  Access the script and inside of the void start function we can put this:

`gameObj = GameObject.FindGameObjectsWithTag("Players");`

This will return us an array that will store all of our GameObjects into the array.

