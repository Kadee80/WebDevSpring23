#HTML5 and Javascript Geolocation:

For this next example, we need to run a local server in order to access the browser’s geolocation settings. For those of you on PC, take a moment and download Brackets. Mac users, you can easily spin up a local server using terminal and a short python command, but you are welcome to use brackets if that feels more comfortable. I will demo how to use both moving forward.

Ever notice how a lot of websites now ask to access your device’s location? This can be very helpful for finding the bank branch near you, or figuring out your local weather forecast. Here is how the do it!

First we check to see if geolocation is supported by the browser, if not we tell the user it is not supported:

```javascript
function getLocation() {
	if (navigator.geolocation) {
		//If geolocation is supported, this code will be executed
	}else{
		alert("Geolocation is not supported by this browser.");
	}
}
```

Now we call another function from the built in geolocation object’s getCurrentPosition method to get the current location:

```javascript
function getLocation() {
	if (navigator.geolocation) {
		navigator.geolocation.getCurrentPosition(showPosition);
	} else {
		alert("Geolocation is not supported by this browser.");
	}
}
```

If the getCurrentPosition method is successful it returns a coordinates object to the function we specify as a parameter.  In the above example the function to execute on success is showPosition( );

Now we need our callback function showPosition:
```javascript
function showPosition(position) {
	console.log(position);
}
```

In this simple example, we are just logging out the coordinates object. The lat lon and accuracy are always returned. Now let’s pull out the lat and lon and show it to the user we can see they are stored within our position object within the coords object. We can access this with dot notation:
```javascript
console.log("Latitude: " + position.coords.latitude + "\nLongitude: " + position.coords.longitude);
```

## To review:

We check to see if the browser/device supports geolocation. If not, we display a message to the user that it is not supported.

If it is supported, we use the built in geolocation object and call method(function) called getCurrentPosition.

The get current position method returns a javascript object with all of the geolocation information which we pass into our callback function showPosition.
showPosition then passes the returned geoposition object into the function as the parameter position.

We can then access different properties within that object using dot (.) notation and display them in the console, to the user, or even pass them into another function as variables.

## Putting it all together – show our current location with Google Maps API

We’ve been using JavaScript Objects a lot already. The geoposition object in the above example is a JavaScript object with many properties within it such as position.coords and that coords property is another JavaScript object within the position object. We can access the coords properties with dot notation. For example: position.coords.latitude.

Now that we have our browser’s location, we can use the Google Maps JavaScript API to display our location on a map.

[First we need an API Key](https://developers.google.com/maps/documentation/javascript/)

Click GET A KEY and follow the instructions.

Once you have an API Key keep that window open, we will need that in a few steps.

[Simple Map Example](https://developers.google.com/maps/documentation/javascript/examples/map-simple)

We will be using a [slightly more complicated example](https://developers.google.com/maps/documentation/javascript/examples/marker-simple) to build off of for today’s exercise. This is a great example if you wish to put a marker in your company’s location on a contact page. Or show the location of a recommended restaurant. We are going to modify this to show our current location on a map.