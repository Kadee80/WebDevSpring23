# User Input as Variables

Lets get the input from a user via the HTML dom. First lets make a simple form inside our `<body>` tag. Lets give a min and max number possible for user. Step= 1 will make sure the user can only input whole numbers, change the step value and see how the UI changes.

```html
<h1> a simple user form </h1>
 <form>
 <fieldset>
 <legend>Pick a number between 0 and 10</legend>
 <input type="number" name="num" id="num" min="0" max="9" step="1">
 <button onclick="userNumber();">See Number</button>
 </fieldset>
```

Notice we are calling a function called userNumber(); on click. Let’s write a function that grabs the user input, passes it into a variable and alerts it to the user again.

```javascript
function userNumber() {
   //get value of form input, first grab the input element by ID
   var userN = document.getElementById("num");
   //then alert out the value of the input using the .value property of the element object
   alert("user input was: " + userN.value);
 };
```

Okay, we now have a function that incorporates user input. But it’s kind of lame. Let’s make it better.

Before we move on, lets clean up our HTML with an event listener. Rather that attaching a function with onclick=”function();” We need to back-track a bit to make this all work.

First, clean up the HTML.
```html
<h1 id="changeMe"> Change me based on the user input!</h1>
 <form>
   <fieldset>
     <legend>Pick a number between 0 and 3</legend>
     <!-- lets give a min and max number possible for user, step 1 will make sure the user can only input whole numbers, change the step value and see how the UI changes -->
     <input type="number" name="num" id="num" min="0" max="3" step="1">
     <button type="button" id="changeBtn" class=".btnClass">Click to change H1 color based on number</button>
   </fieldset>
 </form>
```

First, grab the button by ID, we can also get the element by tag or class name but we will keep it simple for today’s DOM examples:
```javascript
var myBtn = document.getElementById("changeBtn");
```

console log out to see what is returned when we grab an element object from the DOM
```javascript
console.log(myBtn);
```
Why is it null? JavaScript is trying to grab an elementById before that element has finished rendering on the page. We need wrap the above code in an event listener to make sure the DOM is loaded before trying to select  an element from it.

* First, listen for when the DOM is fully loaded.

* The first parameter is the event to listen for “DOMContentLoaded”

* The second parameter is the function to call when the event it detected (Callback Function). Here we are using an anonymous function (these usually show up as callbacks inside other functions). Use anonymous functions when you never need to call a function again.

```javascript
document.addEventListener("DOMContentLoaded", function(){
 var myBtn = document.getElementById("changeBtn");
 //now that we waited for the DOM to finish loading it works! lets log out some individual properties
 console.log(myBtn);
 console.log(myBtn.innerHTML);
 console.log(myBtn.classList);
});
```

Now inside our DOMContentLoaded function, lets add an event listener for our button:

```javascript
myBtn.addEventListener("click", function(){
 //grab our input again
 var userN = document.getElementById("num").value;
});
```

Our input type in our HTML says number. So we think the value returned to JavaScript above should be a number. Let’s double check using typeof:
```javascript
console.log(typeof userN);
```

Well, it’s a String! Let’s convert it to an int so our incoming switch statement will work with just numbers, and we can ditch the quotes. parseInt() will return an Integer from s String. There is also a parseFloat() that returns Floats.
```javascript
var n = parseInt(userN);
console.log(typeof n);
```
Now we have a number to work with!

We are going to change the color class of our H1 based on user input between 0 and 3. Firsts write the CSS classes:

```css
<style>
  h1 {
    text-transform: uppercase;
  }

/* different color classes to apply to our elements via javascript */

  .red {
    color: red;
  }

  .blue {
    color: rgba(0, 0, 255, .75);
  }

  .green {
    color: #00FF00;
  }

  .purple {
    color: rgb(200, 0, 255);
  }
</style>
```

Now place the `<H1>` in a variable so we can change its color with a switch statement:
```javascript
var myH1 = document.getElementById("changeMe");
```
Let’s write our first switch statement. You can read up more on switch statements here.
```javascript
//our first switch statement using the value of a user input,
//rather than having a laundry list of else ifs we can just check cases.
 switch(n) {
 //user inputs the number 0, make H1 red
  case 0:
   myH1.className="red";
   break;
  case 1:
   myH1.className="green";
   break;
 case 2:
  myH1.className="blue";
  break;
 case 3:
  myH1.className="purple";
  break;
 default:
  //do nothing for now, but we could just have a default function here if none of the cases are matched.
 }
```