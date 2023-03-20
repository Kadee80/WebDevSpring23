# Array Objects

Array objects are indexed lists of values. This is great because we can now store multiple values in one variable.

```javascript
var months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
```

Objects or values within the array are separated by commas. When adding the initial values to an array we place them within [];

One of the most useful built in methods for the Array Object is `.length`. This returns the length of the array. Sometimes we need to keep track of the size of an array for looping through it or keeping it below a certain size.

```javascript
console.log(months.length);
```
- console will log 12

There is a built in function to remove the last item of the array. In this example we are removing December from our array and placing it in a separate variable using `.pop();`

```javascript
var lastMonth = months.pop();
 console.log("The last month of the year is " + lastMonth);
 console.log("The arrays length is now " + months.length + " because we removed the last item");
```

Well wait! I was born in December! Let’s put that month back! We can add to the end of an array using `.push(itemToAdd);`

```
months.push(lastMonth);
 console.log("The arrays length is now " + months.length + " because we added December back as the last item");
```

### Accessing individual items in an array via index number:

Sometimes we need to pull out a specific item, or items in an array. We do this using the index of this item:
```javascript
console.log(months[3]);
```

The console will log April. We start by naming the array we wish to access followed by the index number of the item inside square brackets [ ]. *Remember Javascript Array indexes start at 0 not 1!*

## Review –  For loop structure:

```javascript
for (var i = 0; i < 10; i++) {
 console.log(i);
 };
```

`var i = 0;`
is statement 1. This is the initial value of the variable i and we delare and assign it value here.

`i < 10;`
is statement 2. This is the condition to check for while the loop is running. As long as this statement evaluates to true, the loop will continue.

`i++`
is statement 3. This is the statement or action to perform once the block of code within the {} of the loop has been executed.  In this example, we are incrementing i by after we finish console logging the current value of i.

`console.log(i);`
is the block of code to execute when the second statement (the conditional) evaluates to true.

We can achieve the same result with an if else statement as well. But the for loop is a little cleaner right?
```javascript
var i = 0;
 if (i < 10){
 console.log(i);
 i++;
 };
```
is the same as:
```javascript
for (var i = 0; i < 10; i++) {
 console.log(i);
 };
```
## Putting it all together-  looping through an array:

Sometimes we need to access all items in an array in order and then perform some other task with the data returned. We can do this using a for loop.
```javascript
for (var i = 0; i < months.length; i++){
 console.log(months[i]);
 };
```
We set i to equal 0 to start – array indexes start at zero.

Our condition is checking to make sure i is less than the length of the array. If we chose an arbitrary number here we run into problems.

Either the arbitrary number is bigger than the length of the array, resulting in an out of bound exception error. We can’t grab an item from an array that doesn’t exist right?

Or we chose an number too small, and we wont loop through the entire array.
`i++` increments the index by 1. If our third statement was i+=2, we would only log every other month in our months array.

`console.log(months[i]);``  is logging the value of the array item at the index position of i.

We can also loop through arrays backwards. This is great when you are systematically deleting items in an array. We start at the initial length of the array here and decrement by 1 each time in order to avoid the out of bound exception listed above. By the end of this loop we have emptied our array.

```javascript

for (var i = months.length - 1; i >= 0; i--) {
 var dMonth = months.pop();
 console.log("Deleted "+ dMonth +"new array length is: " + months.length);
 };
```