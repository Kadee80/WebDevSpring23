# JavaScript Math Methods

Let's take a look deeper at two of JavaScript’s number data types: **Floats** and **Integers** and some built in JavaScript methods we can use with them.

### To review:
Integers are whole numbers, and Floats are floating point numbers (decimal numbers).

## Integers + Simple Math Calculations

First, inside a `<script>`` tag in the `<head>` of our document, let’s declare some global variables. You can read more about variable scope here.

```
var x = 15;
var y = 35;
```

Notice both of these variables start off as Integers. We will introduce Floats in a bit.

Now we can perform some simple math operators and log them out to our console. Notice how similar to algebra this all looks:

addition +
```
  console.log(x + y);
```

subtraction -
```
  console.log(y - x);
```
multiplication *
```
  console.log(x * y);
```
division /
```
 console.log(y / x);
```

Lets also take a look at the modular operator.  The *modular operator* `%` returns the division remainder. This is helpful if we want to use even numbers, or every nth number by checking remainders.
```
console.log(y % x);
```

35/15 is 2 with a remainder of 5. Modulo will return the remainder 5!

We can also write longer math expressions just like we did in algebra. Here to execute our addition first we need to group it in parentheses.

```
console.log((x + y) * y - 1);
```

## Incrementing and Decrementing Numbers

Sometimes we need to increase or decrease a number by 1, or any other number. Perhaps for a counter of sorts, or in a for loop.

 increment by 1 ++
 ```
 x++;
 console.log(x);
 ```

 increment by any other number +=N
 ```
 x = x += 5;
 console.log(x);
 ```

 we can also decrement by 1 or any other number
 ```
 y--;
 console.log(y);

 y = y -= 5;
 console.log(y);
 ```

## Floating point number data types and Built in Math Functions

We can access JavaScripts Math object’s built in methods (functions) at any time using the Math Object name and then dot notation to access an individual method We will go over JavaScript Objects and JSON soon, and all will be much clearer.

Declare var z and assign it a floating point value
``` 
 var z = 2.25; 
```
 
#### Math.floor() rounds a float DOWN to nearest Int
```
 var zf = Math.floor(z);
 console.log(zf);
```
 
Declare var n and assign it a floating point value
```
var n = 5.35; 
```

#### Math.ceil() rounds a float UP to nearest Int
```
var nc = Math.ceil(n);
console.log(nc);
```

#### Math.round() rounds up or down to the nearest whole number
```
var num1 = 2.2;
var num2 = 2.7;
console.log(Math.round(num1));
console.log(Math.round(num2));
```

### Math.random(); When in doubt grab a random number!

Math.random returns a random float between 0 and 1
```
var r = Math.random();
console.log(r);
```

We can use Math.round combined with Math.random to get a random 0 or 1 (good for either/or – true false situation);
```
var yn = Math.round(Math.random());
console.log(yn);
```

We can now combine this with an if/else statement based on our random result if our random number rounds up or down. A single = sets a variable to a value. To compare we need t0 use ==. Take a look at JavaScript Comparisons Here.
```
//alert no if the var yn rounds down to 0.
 if (yn == 0) {
 alert("No!");
 }
 //if it does not round down, it must round up to 1, in that case alert yes
 else {
 alert("Yes!");
 }
```

The case above works fine for an either/or situation. But what if we want a random number between 0 and 10?

Let’s make this a function with a number parameter so we can change the range whenever we want:
```
function randomNumber(n) {
  //when we declare a variable inside a function, this variable "dies" 
  //aka can't be used outside of the function. take a look at JavaScript Scope for more info.
  var rn = Math.round(n * Math.random(n));
  console.log(rn);
 }

 // After we declare a function we have to call it in order for it to execute. 
 // Don't forget to pass in a number parameter
randomNumber(25);
```
Cool. But that only covers random numbers between 0 and N. What if we want to enter a min and max range? We need to use a few of our simple math operators to accomplish this:
```
 //random number within the range provided in min and max parameters
 function randNumRange(min, max) {
 //here we have to add a few math expressions to make sure our range starts at the min number
 var rn = Math.round(Math.random() * (max - min) + min);
 console.log(rn);
 //by retuning the value of RN in the function we can use this random generated number anywhere we call it. we can assign it to a variable in the future
 return rn;
 };
 //call the function
 randNumRange(3, 5);
```

If we have time, we will use random() to pick random elements from an array!

