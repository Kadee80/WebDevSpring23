## Transform 2D:

Today’s in class demo is going to take a look at a few 2D transformations:

* transform: translate(x,y);
* transform: rotate(#deg);
* transform: scale(2);
* transform: scale(x,y);
* transform: skew(x#deg,y#deg);
* transform: skewX(#deg)
* transform: skewY(#deg);

We will go through this in the class demo, but they are pretty straight forward! You can always review the W3 Schools CSS Transform 2D section for more info.

## Transform 3D:

Let’s just take a moment, and look at a demo that shows the difference between rotating in 2D and rotating in 3D along either the X, Y, or Z axis.
```html
<!DOCTYPE html>
<html>

<head>
 <title>CSS3 Transforms</title>
 <style>
 div {
 background-color: rgba(0, 0, 255, 0.3);
 color: #00f;
 width: 300px;
 height: 300px;
 display: inline-block;
 margin: 20px;
 }
 
 .rotX {
 -webkit-transform: rotateX(130deg);/* Safari */
 transform: rotateX(130deg);
 }
 
 .rotY {
 -webkit-transform: rotateY(130deg); /* Safari */
 transform: rotateY(130deg);
 }
 
 .rotZ {
 -webkit-transform: rotateZ(130deg);/* Safari */
 transform: rotateZ(130deg);
 }
 </style>
</head>

<body>
 <div class="rotX"><p>This div rotates 3D along the X axis</p></div>
 <div class="rotY"><p>This div rotates 3D along the Y axis</p></div>
 <div class="rotZ"><p>This div rotates 3D along the Z axis</p></div>
</body>

</html>

```

## CSS3 Transitions:

With transitions, we can change from one style property to another smoothly over time. All we need to define is the property we wish to change and the duration of the transition. In this example, when a user hovers over the red div it will turn green over the course of 2 seconds:

```css
.redgreen{
  width:100px;
  height:100px;
  background: red;
  -webkit-transition: background 2s; /* Safari */
  transition: background 2s;
}

.redgreen:hover{
  background:green;
}
```
## Live Code:

Do a quick `git pull` of this repo and copy the In_Class_Starter folder from this section into your HW/Classwork repo so we can get started.

## In class Exercise:

Based on the live code we work on together today, make all of the CSS3 transforms we coded in only visible on hover. Be sure to explore different timing, delays, and speed curves. Check out the documentation on transitions to learn how to do this:

[W3 Schools CSS3 Transitions](http://www.w3schools.com/css/css3_transitions.asp)

