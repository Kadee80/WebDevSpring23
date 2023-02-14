# Media Queries: an Introduction 

We use media queries to define different styles for different types of media and different screen sizes and layouts. When the conditions defined in the media query evaluate to TRUE, the corresponding styles are applied.

```css
body{
 	background-color:red;
}
@media (max-width:960px){
	body{
		background-color: black;
	}
}
```
In this example, the default browser window background color will be red. However as we resize the screen, and our browser is now less then 960px wide, the `(max-width:960px)` condition is now true. The browser background will now have the new style definitions applies and the window will turn black.

## Common Media Query Templates 

#### **Mobile First** using only min-width. 

Note you have to start with mobile FIRST. If we reverse the order of these queries, mobile styles will override all previous definitions. 

Why? Because even a big screen satisfies the minimum width of 320px. 
```css
/* smartphones, iPhone, portrait 480x320 phones */ 
	
	@media (min-width:320px) { 
	
	}

 /*portrait e-readers (Nook/Kindle), smaller tablets @ 600 or @ 640 wide. */
	@media (min-width:481px) {  

	}
/* portrait tablets, portrait iPad, landscape e-readers, landscape 800x480 or 854x480 phones */
	
	@media (min-width:641px) { 

	}
/* tablet, landscape iPad, lo-res laptops ands desktops */
	
	@media (min-width:961px) { 

	}
/* big landscape tablets, laptops, and desktops */
	
	@media (min-width:1025px) {  

	}
/* hi-res laptops and desktops */
	
	@media (min-width:1281px) {

	}
```
#### **Desktop First** using min-width and max-width:

If you wish to design for desktop first and then work backwards towards mobile devices you can define a minimum and maxium width to make sure your styles apply within a range. In this example, we write the default large screen styles (desktop, hi-res). And then work backwards to smaller and smaller screens we with to support. 

*These media queries we developed by Josh Cope to work with the Responsive 996px grid system 

```css
/* Tablet Portrait size up to 996px */
	
	@media only screen and (min-width: 768px) and (max-width: 995px) {

	}

/* Common Mobile Sizes */
	
	@media only screen and (max-width: 767px) {

	}

/* Mobile Landscape Size to Tablet Portrait */
	
	@media only screen and (min-width: 480px) and (max-width: 767px) {

	}

/* Mobile Portrait Size to Mobile Landscape Size */
	
	@media only screen and (max-width: 479px) {

	}
```

## LIVE CODE - Mobile | Tablet | Desktop -layouts with Breakpoints  

For today's demo, we are going to design a desktop screen layout, and then add in 2 responsivbe media breakpoints to change how our layout displays on tablets and cellphones.

This example lumps all tablets into a general size range, and all phones into a general size range. When you design and build for a client, you should take into account specific use cases. The goal is to support as many devices as possible, while not driving yourself insane with overly specific queries.

Before we begin. Do a `git pull` from the class repo. 

You will see these breakpoints already provided in the style.css file in today's in class starter.

```css
/* Write your default styles first. Then as the media queries return TRUE, styles will be updated/overidden. */

/* Any screen over 1024px wide will have the defaults applied */
    
    body{
        background-color: red;
    }

/* Our generic clear fix to avoid wrapping issues when we float. Notice we make sure this is applied in the default style section. */
    
    .clear-fix:after {
        display: block;
        clear: both;
        /* ensure some older compatability */
        height: 0;
        font-size: 0;
        content: " ";
        /* extra backup */
        visibility: hidden;
    }

/* Tablet */

    @media only screen and (min-width: 768px) and (max-width: 1024px) {
        body {
            background-color: green;
        }
    }
    
    /* Take a look at this one! It queries the device height and width rather than the browser window. Notice how this only works when we use developer tools to fake a tablet's specs.*/

    @media only screen and (min-device-width: 768px) and (max-device-width: 1024px) { 
        body {
            background-color: yellow;
        }
    }  
    
    /* Smaller Screens, Mobile  */
    
    @media only screen and (max-width: 767px) {
        body {
            background-color: blue;
        }
    }
```