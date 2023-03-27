# JavaScript Objects and JSON

– Javascript Object Notation.

The next exercise will involve accessing JavaScript Objects and their properties. Before moving on let’s write our own JavaScript object and access the properties and their individual variables.

Let’s make a variable to hold our javascript object called customer:
```javascript
var customer = {};
```

Right now, customer is an empty object. So let’s add a few simple properties:
```javascript
var customer = {
	firstName : "Tony",
	lastName : "Pony"
};
```
Each property consists of a key and a value, or a key value pair. The syntax is:
```javascript
var myVar = {
	key : value,
	key : value
}
```
The key value pairs are separated by commas “,” just like in an Array. Remember to not add a comma after the last key value pair. The values can be Strings | Integers | Floats | Arrays | other Objects or even Functions. Let’s add some more properties to our customer object. We can do this 2 different ways:

Add an array to our pets key we declare the object:
```javascript
var customer = {
	firstName : "Tony",
	lastName : "Pony",
	pets : ["Dog", "Cat", "Iguana"]
};
```

Access the firstName property with dot notation
```javascript
console.log(customer.firstName);
```
Access the second pet in the array
```javascript
 console.log(customer.pets[1]);
```

Add an Integer to our customer object later on in our code (maybe we needed some user form input, or to access our users current geolocation before assigning this property a value):

Add a new property later in our code with dot notation
```
customer.age = 45;
//log out the entire object to see our added property
console.log(customer);
```

##In Class Exercise:

1- Make a new HTML file with a `<script` tag in the head of your document

2- Put the following JavaScript Object at the top of your script tag:

```
var myClass = { 
	me: {
		firstName: "Tony",
		lastName: "Pony",
		pets: ["Dog", "Cat", "Iguana"]
	},
	others: [
		{
		firstName: "Sally",
		lastName: "Omally",
		pets: ["ButterFly", "Bird"]
		},
		{
		firstName: "Billy",
		lastName: "Goat",
		pets: ["Snake", "Fish"]
		},
		{
		firstName: "Tara",
		lastName: "Ohara",
		pets: ["Gecko", "Lizard"]
		}
	]
};
```

3- Using `console.log();` and dot notation print out the following to the console:

	1- Tony’s third pet
	2- Billy’s last name
	3- The size of the others array
	4- The first name of everyone in the others array (for loop and array.length is needed)
	5- Tara’s first pet