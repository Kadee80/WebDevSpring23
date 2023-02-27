# Hello World! (Again - but this time with JavaScript)

Today we will begin learning JavaScript. This is very exciting, because we can now start adding more interactivity to our pages. We can create (or destroy) HTML elements, assign (or remove) css styles to different elements on our page, perform calculations, start storing data from a users input, and so much more. Once we have become comfortable with pure JavaScript we can start utilizing external libraries and get really creative with our websites.

We can add small scripts to individual pages using the script tag in either the `<head>` or `<body>` of our HTML:
 
```html
<!DOCTYPE html>
<html>
<head>
 <title>Hello World</title>
 <script type="text/javascript">
 alert("Hello World!");
 </script>
</head>
<body>
</body>
</html>
```
This is fine if you only want to use a function once, but usually you want to share functions across your entire site. Just like we can link to an external stylesheet .css file, we can link to an external .js file:

```html
<!DOCTYPE html>
<html>
<head>
 <title>Hello World</title>
 <script src="main.js"></script>
</head>
<body>
</body>
</html>
```
Before we start coding, we need to remember that JavaScript does not have any built in display functions.

It does however have a few useful built in functions to help us see our data, check our functions, or check for errors. Today will will be using:

* `alert();` – displays a pop up window with the data we pass in to the ()
```
alert(“Hello World!”);
```

* `console.log();` – logs data to the javascript console (we can access this with Google Developer Tools or Firebug)
```
console.log(“this is my first console log!”);
```

* `.innerHTML` – change the text between the opening and closing tags of an HTML element of our choosing.
```
document.getElementById("output").innerHTML = "I just changed the content of this div using JavaScript";
```

## Syntax:

* Each statement (program instruction) ends with a semi-colon ;

### Variables:

Variables are containers for storing data values. Today we will work with:

* Strings:  “Some Text”

* Integers:  27

* Floats:  27.934

Basically, letters and numbers. But many other data types can be stored in a javascript variable, like arrays objects functions and classes. We will learn more about these data types later.

*Sometimes we just need to use some text or a number that won’t change over time. Fixed values in Javascript are called literals.*

Before using a variable, we have to declare (create) it:

```
var myName;
```

Right now, myName is just an empty placeholder until we assign it a value. We can do that right away, or later on in a specific function. To assign a value to a variable we use =

```
myName = “Katie”
```
We can not assign a value to a variable without declaring it first!

We can declare and assign a variable a value simultaneously like so:

```
var myName = “Katie”;
```
It is good practice to declare all of your variables at the beginning of your script!

“Katie” is a String. Strings are text values wrapped in either double “” or single ’’ quotes.

Integers are whole numbers, and Floats are decimal numbers.

```
var myInt = 10;
var myFloat = 10.1;
```

For those of you who have written in other programming languages, you will notice you do not have to declare a variable *type* in JavaScript. This makes variables more flexible, but you can also run into trouble down the road if you are not careful.

### Expressions:

An expression is a combination of values, variables, and operators, which computes to a value. The computation is called an evaluation.

`2+2` (evaluates to 4)

Don’t worry too much about the vocabulary right now, but we will be doing a lot of math with expressions in our code moving forward.

We can use expressions to do calculations within functions, or to assign a variable a value:

`console.log(4+4);`
– logs 8

```
var x = 4; -4
var y = x-1; -3
var z = x*y; -12
console.log(z);
```

Starting to look like algebra right? Here is a list of js arithmetic operators.

There are a lot of built in functions (methods) we can use with Strings or Numbers. When you have time take a moment to review them.

### Converting Data Types

I mentioned earlier that since var can hold any kind of variable we may run into trouble from time to time. Sometimes you may have a number in a String variable, or a String in a Float variable. You can see how this might get messy when you try and do a calculation with text, or use a String method on a number. Luckily, we can convert between the different variable types with some built in methods.

```
var myVar = “number”;
```

The “” tell JavaScript to expect a String. Later in your code you may reassign the value of myVar:

```
myVar = 4+4;
```

So what happens when you want to double myVar?

```
myVar = myVar*2;
```

myVar is now “8” not the number 8! JavaScript will usually “know what you meant” and just do the calculation anyway, but sometimes this little slip up can really break a whole script. To get around this we can use a built in method called parseFloat()
```
myVar = parseFloat(myVar);
```
We can also turn a number into text using the toString() method:

```
var myInt = 23;
var myString = myInt.toString();
```

[W3 Schools Data Type Tutorials](http://www.w3schools.com/js/js_datatypes.asp)

### Combining Variables and Strings

Sometimes we want to perform a calculation and display that somewhere within text or Strings. This is a useful way to keep track while debugging code or display information in a clear way to a user. We can insert variables into text strings like so:

```
var temp = 73;
console.log("Todays temperature is " + temp + " degrees F.");
```

##Functions

###Syntax

Functions contain the “function” keyword, followed by a function name of your choosing, followed by parenthesis () where parameters can be passed into our function. The code for the function to execute is then listed within the curly brackets {}:

```
function myFunctionName (parameter1, parameter2){
 //javascript statements for this function here
 }
```

A JavaScript function is a block of code which performs a particular task. Functions need to be invoked in order to execute. This is usually done when a particular event occurs or when it is called within another function. You will see in our demos today that we can’t just simply declare variables and write functions and expect it to execute. w3 Schools Functions Explained

####Function firing when a button is clicked:
```html
<!DOCTYPE html>
<html>
<head>
 <title></title>
 <script type="text/javascript">
 function sumValues(a,b){
 var sum = a+b;
 console.log("Your total charges are: " + sum +".");
 }
 </script>
</head>
<body>
 <button onclick="sumValues(7,23.6);">View Total</button>
</body>
</html>
```

Notice in the above example, we have to attach the function to the onclick event listener. We are passing the numbers 7 and 23.6 in as our two parameters a and b to our function. There are many other event listeners. You can view them here. We could also pass values in from a form or some other user input as variables. Here they are hardcoded in.

####Functions being called when a page loads:
```html
<!DOCTYPE html>
<html>
<head>
 <title></title>
 <script type="text/javascript">
 function sumValues(a,b){
 var sum = a+b;
 console.log("Your total charges are: " + sum +".");
 }
 </script>
</head>
<body onload="sumValues(12.2 , 17.74)">
</body>
</html>
```

Here we called a function when the body of our HTML page has loaded.

We can also call functions within functions. Sometimes you want many different functions to invoke when the page loads, but you may want to use them separately again later.

```html
<!DOCTYPE html>
<html>

<head>
 <title></title>
 <script type="text/javascript">
 function startMe() {
 	sumValues(56.7, 34.6);
 }


 function sumValues(a, b) {
 var sum = a + b;
 console.log("Your total charges are: " + sum + ".");

 }
 </script>
</head>

<body onload="startMe();">
 <button onclick="sumValues(235,3756);">Click Me</button>
</body>

</html>
```

### Boolean Function and Comparisons

Sometimes we need data types to only return TRUE or FALSE. For example, has the user entered all of their data in the form correctly? or is a clickable element displayed in the ON or OFF position? We can do this with JavaScript Boolean function but we usually use Comparisons and Conditionals.

```html
<!DOCTYPE html>
<html>

<head>
 <title></title>
 <script type="text/javascript">
 //This global variable is a boolean. it can only be null, true, or false
 var isOn = true;
 
 function switchOnOff() {

	 if (isOn == true) {
		 alert("isOn is set to true. Switching to false now.");
		 isOn = false;
	 } else {
		 alert("isOn is set to false. Switching to true now.");
		 isOn = true;
	 }

 }
 </script>
</head>

<body >
 <button onclick="switchOnOff()"> Click me Switch the Boolean Variable back and Forth</button>
</body>

</html>
```


## For Loops

Sometimes you need to perform a task/function multiple times. Rather than writing the same statement over and over in a function, we can use use a Loops for this. There are several kinds of loops you can read more about them here. Today we will look at a simple for loop.

```js
for (statement 1; statement 2; statement 3) {
    code block to be executed
}
```

Statement 1 is executed before the loop (the code block) starts. This is usually when we set an intital number for our counter.

Statement 2 defines the condition for running the loop (the code block). As long as the condition is TRUE the code will keep executing. Beware of infinite loops!

Statement 3 is executed each time after the loop (the code block) has been executed. This is usually where we increment our counter.

Here we are passing in the number 25 to our for loop with the parameter n. The code inside our for loop with execute 25 times. Notice how the console.log() stops at 24. That is because the the loop only executes while the number is less than 25.

```html
<!DOCTYPE html>
<html>

<head>
 <title></title>
 <script type="text/javascript">
	function countToN(n){
		for (var i = 0; i < n; i++) {
			console.log(i);
		};
	}

 </script>
</head>

<body >
 	<button onclick="countToN(25);">Click Me to Start the Loop</button>
</body>

</html>
```

You will notice in the above code. The third statement in our for loop is:

```
i++;
```
Using ++ or — we can increment or decrement the value of i by 1. It is shorthand for writing:

```
i = i+1;
```
If we want to increment or decrement by another number it is written like so:

```
i+=2;
j-=10;
```
These larger increments are great for alternating odd and even numbers or doing cool pixel manipulations.

Next class we will look at JavaScript Arrays and the true power of the for loop will be revealed!