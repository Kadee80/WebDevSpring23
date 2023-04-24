# SASS Intro

Today we will be building a responsive navbar using SASS. [SASS](http://sass-lang.com/) is a Ruby Gem we need to [install on our computer](http://sass-lang.com/install). Today we will just be compiling our stylesheets using SASS command line. However, when working on a Ruby on Rails project, I much prefer to use [Compass](http://compass-style.org/) to watch and compile my stylesheets in the background.

For those of you who did not install SASS and RUBY over the weekend, you will have to use an [online SASS compliler](https://www.sassmeister.com/) for todays lesson.

###Install SASS using command line:

```bash
gem install sass
```

If it does not install, and you receive an error you need to install as admin on your computer. `sudo` will always prompt you for your computers password:

```bash
sudo gem install sass
```

Check your version and confirm SASS is installed:

```bash
sass -v
```

## Building Our Nav:

Take a look at the `In_Class` folder. You will see we have an unstyled header and nav bar:

```html
<header>
  <a href="#" class="brand">
    <!-- this could also easily be a logo img, we just need to style accordingly -->
    <h1 class="top-nav-logo">Goats-R-Us</h1>
  </a>
  <nav>
    <ul id="main">
      <li>
        <a href="" class="menu-toggle" data-dropdown=".products">Products</a>
      </li>
      <li>
        <a href="" class="menu-toggle" data-dropdown=".company">Company</a>
      </li>
      <li>
        <a href="" class="menu-toggle" data-dropdown=".resources">Resources</a>
      </li>
      <li>
        <a href="">Buy</a>
      </li>
    </ul>
    <section id="dropdown">
      <ul class="products">
        <li class="mobile">Products</li>
        <li><a href="#">Link</a></li>
        <li><a href="#">Link</a></li>
        <li><a href="#">Link</a></li>
        <li></li>
      </ul>
      <ul class="company">
        <li class="mobile">Company</li>
        <li><a href="#">Link</a></li>
        <li><a href="#">Link</a></li>
        <li><a href="#" target="_blank">Link</a></li>
        <li><a href="#">Link</a></li>
      </ul>
      <ul class="resources">
        <li class="mobile">Resources</li>
        <li><a href="#">Link</a></li>
        <li><a href="#">Link</a></li>
        <li><a href="#">Link</a></li>
        <li><a href="#" target="_blank">External Link</a></li>
      </ul>
    </section>
  </nav>
  <!-- <br style="clear:both"> -->
</header>
```

## Nested Styles

The example below is a very basic example of nested styles using SASS. We will build off of this example for the rest of class. But first, lets take a look at this nested structure.

```scss
header {
  background: #fff;
  padding: 10px 0;
  position: fixed;
  width: 100vw;
  z-index: 100;
  font-size: 12px;
  background: rgba(255, 255, 255, 1);
  background: linear-gradient(
    to bottom,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 96%,
    rgba(230, 230, 230, 1) 100%
  );
  &:after {
    display: block;
    clear: both;
    /* ensure some older compatability */
    height: 0;
    font-size: 0;
    content: ' ';
    /* extra backup */
    visibility: hidden;
  }
  a.brand {
    display: block;
    height: 100%;
    width: 200px;
    margin: 0 20px;
    float: left;
    text-decoration: none;
    transition: all 0.4s linear;
    color: #006fff;
    line-height: 40px;
    h1 {
      font-weight: 200;
      margin: 0;
      padding: 0;
      font-size: 30px;
    }
  }
}
```

Here we are styling our `header` element. Inside our header, we have an `anchor` tag with the class brand. Inside our `a.brand` we have an `h1`. This nesting directly resembles our html right?

```html
<header>
  <a href="https://opentrons.com" class="brand">
    <h1 class="top-nav-logo">Goats R Us</h1>
  </a>
  ...
</header>
```

**A note on `&`:**

Inside our header we also see some slightly different syntax:

````scss
header {
  //these styles apply to header
  &:after {
    //these styles will compile to header:after
  }
}

ifwewant to style an element, and then that element + a more specific selector, we add it using `&`. Another example might be: ```scss
  a {
  //these styles apply to all anchor tags
  &.active {
    //these styles will compile to a.active
  }
}
````

### Compiling SASS to CSS

So we have the very beginning of a nested style sheet. Before we talk about CSS specificity, lets compile what we have into CSS and compare the differences.

To compile SASS:

```bash
cd [your-site-directory]
sass [sass-folder-name/sass-file-name] [css-folder-name/css-file-name]
```

The command above tells our computer:
Use SASS (The ruby gem we installed) to compile _this_ SASS file into _that_ CSS file.

So for our project:

```bash
sass sass/main.scss css/main.css
```

Lets take a look at how this compiled:

```css
body {
  margin: 0;
  padding: 0;
  background-color: #ddd;
  font-family: 'Helvetica Neue', Arial sans-serif;
}

header {
  background: #fff;
  padding: 10px 0;
  position: fixed;
  width: 100vw;
  z-index: 100;
  font-size: 12px;
  background: white;
  background: linear-gradient(to bottom, white 0%, white 96%, #e6e6e6 100%);
}

header:after {
  display: block;
  clear: both;
  /* ensure some older compatability */
  height: 0;
  font-size: 0;
  content: ' ';
  /* extra backup */
  visibility: hidden;
}

header a.brand {
  display: block;
  height: 100%;
  width: 200px;
  margin: 0 20px;
  float: left;
  text-decoration: none;
  transition: all 0.4s linear;
  color: #006fff;
  line-height: 40px;
}

header a.brand h1 {
  font-weight: 200;
  margin: 0;
  padding: 0;
  font-size: 30px;
}

@media (max-width: 768px), screen and (max-device-width: 768px) {
  header {
    padding: 5px 0px 0px 0px;
    background: none;
    background-color: white;
  }
  main {
    padding: 2.5vh;
    padding-top: 50px;
    height: 60vh;
    background-color: black;
    color: white;
  }
}
```

Our nested styles compile to some pretty specific css selectors. Before we write the rest of our styles, lets do a quick exercise regarding `CSS Specificity`.

**Pro Tip: Knowing CSS Specificity will help you ace a front end dev job interview**

## CSS Specificity: Aka why isn't my style showing up?

CSS stands for Cascading Style Sheets. The most recently applied style should always apply right? Not neccessarily. A more specific rule will always override a more generic style, regardless of where it exisits in your style sheet.

### Specificity Math:

Specificity rules are dead simple.

- html element selectors = 1 point

- class selectors = 10 points

- ID selectos = 100 points

For example

`header a.brand` has 2 html tags and 1 class: 2+10 = 12.

`header nav ul li a.active` has 5 tags and 1 class: 5+10 = 15.

The most specific selector will always override its counterparts. So if we wanted to override `header nav ul li a.active` we could add an ID into the mix for more specificity points:

`header nav#menu ul li a.active` 5+10+100 = 115!

Let's take a moment to do a few of these together:

```css

header a.brand

header a.brand.open

header a.brand h1

header nav section#dropdown ul

header nav section#dropdown ul li.mobile

header nav section#dropdown ul li a:hover

header nav section#dropdown ul.active li a

div#nav-collapse.change .bar3
```

## Live Code, Responsive Navbar with SASS

If we dont want to keep compiling via command line, we can use sass watch:

```
sass --watch sass:css
```

Here we are telling SASS to watch for changes in our sass folder and write it to our css folder.

To cancel the watch command: `control + c`
