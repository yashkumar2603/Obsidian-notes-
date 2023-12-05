To make the basic structure studied in [[HTML; Lecture-0.]] elegant and pleasing to the eye, we use CSS.

CSS - Cascading Style Sheets 

There are far too many CSS properties to go over here, but just like HTML elements, it’s typically easy to Google something along the lines of “change font to blue CSS” to get the result. Some of the most common ones though are:
- `color`: the color of text
- `text-align`: where elements are placed on the page
- `background-color`: can be set to any color
- `width`: in pixels or percent of a page
- `height`: in pixels or percent of a page
- `padding`: how much space should be left inside an element
- `margin`: how much space should be left outside an element
- `font-family`: type of font for text on page
- `font-size`: in pixels
- `border`: size type (solid, dashed, etc) color

#### CSS style selectors :

- There are many ways to determine which HTML elements you are styling, some of which we’ll mention here:
    - **element type**: this is what we’ve been doing so far: styling all elements of the same type.
    - **id**: Another option is to give our HTML elements an id like so: `<h1 id="first-header">Hello!</h1>` and then applying styling using `#first-header{...}` using the hashtag to show that we’re searching by id. Importantly, no two elements can have the same id, and no element can have more than one id.
    - **class**: This is similar to id, but a class can be shared by more than one element, and a single element can have more than one class. We add classes to an HTML element like this: `<h1 class="page-text muted">Hello!</h1>` (note that we just added two classes to the element: `page-text` and `muted`). We then style based on class using a period instead of a hashtag: `.muted {...}`
- Now, we also have to deal with the problem of potentially conflicting CSS. What happens when a header should be red based on its class but blue based on its id? CSS has a specificity order that goes:
    1. In-line styling
    2. id
    3. class
    4. element type
- In addition to the comma for multiple selectors, there are several other ways to specify which elements you would like to style. This table from lecture provides a few, and we’ll go through a few examples below:
- ![[Pasted image 20230829195121.png]]

**Attributes as Selectors**: We can also narrow down our selection based on the attributes we assign to HTML elements using brackets. For example, in the following list of links, we choose to only make the link to Amazon red:
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Using Selectors</title>
        <style>
            a[href="https://www.amazon.com/"] {
                color: red;
            }
        </style>
    </head>
    <body>
        <ol>
            <li><a href="https://www.google.com/">Google</a></li>
            <li><a href="https://www.amazon.com/">Amazon</a> </li>
            <li><a href="https://www.facebook.com/">Facebook</a></li>
        </ol>

    </body>
<html>
```

So now, only the one the one with the specific href gets the styling.

##### Hover : (situational/ conditional styling)

- Not only can we use CSS to change what an element looks like permanently, but also what it looks like under certain conditions. For example, what if we wanted a button to change color when we hover over it? We can achieve this using a [CSS pseudoclass](https://www.w3schools.com/css/css_pseudo_classes.asp), which provides additional styling during special circumstances. We write this by adding a colon after our selector, and then adding the circumstance after that colon.
- In the case of the button, we would add `:hover` to the button selector to specify the design only when hovering:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Pseudoclasses</title>
        <style>
            button {
                background-color: red;
                width: 200px;
                height: 50px;
                font-size: 24px;
            }

            button:hover {
                background-color: green;
            }
        </style>
    </head>
    <body>
        <button>Button 1</button>
        <button>Button 2</button>
        <button>Button 3</button>

    </body>
<html>
```

So now the button change colors upon hovering over them.

**There are many libraries, tools and languages developed to write the CSS codes less redundantly and more easily some of which are : **
* [[Bootstrap; Lecture-0.]]
* [[SASS; Lecture-0.]]
