- One way we can achieve this is through knowledge of the **viewport**. The viewport is the part of the screen that is actually visible to the user at any given time. By default, many webpages assume that the viewport is the same on any device, which is what leads to many sites (especially older ones) being difficult to interact with on mobile devices.
- One simple way to improve the appearance of a site on a mobile device is to add the following line in the head of our HTML files. This line tells the mobile device to use a viewport that is the same width as that of the device you’re using rather than a much larger one.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- Another way we can deal with different devices is through [media queries](https://www.w3schools.com/cssref/css3_pr_mediaquery.asp). Media queries are ways of changing the style of a page based on how the page is being viewed.
- For an example of a media query, let’s try to simply change the color of the screen when it shrinks down to a certain size. We signal a media query by typing `@media` followed by the type of query in parentheses:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Screen Size</title>
        <style>
            @media (min-width: 600px) {
                body {
                    background-color: red;
                }
            }
            @media (max-width: 599px) {
                body {
                    background-color: blue;
                }
            }
        </style>
    </head>
    <body>
        <h1>Welcome to the page!</h1>
    </body>
</html>
```

This code changes the colour of the page background based on the size of the viewport.

*  Another way to deal with differing screen size is using a new CSS attribute known as a **[flexbox](https://www.w3schools.com/css/css3_flexbox.asp).** This allows us to easily have elements wrap around to the next line if they don’t fit horizontally. We do this by putting all of our elements in a `div` that we’ll call our container. We then add some styling to that div specifying that we want to use a flexbox display for the elements inside of it. We’ve also added some additional styling to the inner divs to better illustrate the wrapping that’s occuring here.
```html
<head>
        <title>Screen Size</title>
        <style>
            #container {
                display: flex;
                flex-wrap: wrap;
            }

            #container > div {
                background-color: green;
                font-size: 20px;
                margin: 20px;
                padding: 20px;
                width: 200px;
            }
        </style>
    </head>
    <body>
        <div id="container">
            <div>Some text 1!</div>
            <div>Some text 2!</div>
            <div>Some text 3!</div>
            <div>Some text 4!</div>
            <div>Some text 5!</div>
            <div>Some text 6!</div>
            <div>Some text 7!</div>
            <div>Some text 8!</div>
            <div>Some text 9!</div>
            <div>Some text 10!</div>
            <div>Some text 11!</div>
            <div>Some text 12!</div>
        </div>
    </body>
```

Now, in the #container styling, the flex ttells that the flex-box is enabled, and the flex-wrap type specified is  'wrap', which more or less works  just like text wrapping did in MS Word.
This wrapping will allow for them to assume column formation and adjust the number of rows depending on the space available.

**Another Popular way of doing this is using HTML grids**
```html
 <head>
        <title>My Web Page!</title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <style>
            .grid {
                background-color: green;
                display: grid;
                padding: 20px;
                grid-column-gap: 20px;
                grid-row-gap: 10px;
                grid-template-columns: 200px 200px auto;
            }

            .grid-item {
                background-color: white;
                font-size: 20px;
                padding: 20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <div class="grid">
            <div class="grid-item">1</div>
            <div class="grid-item">2</div>
            <div class="grid-item">3</div>
            <div class="grid-item">4</div>
            <div class="grid-item">5</div>
            <div class="grid-item">6</div>
            <div class="grid-item">7</div>
            <div class="grid-item">8</div>
            <div class="grid-item">9</div>
            <div class="grid-item">10</div>
            <div class="grid-item">11</div>
            <div class="grid-item">12</div>
        </div>
    </body>
```

In this line, 
`grid-template-columns: 200px 200px auto;`
we specified that only the width of the 3rd column is going to be auto, not the rest, we can use auto in all to have even shifting.
also we can combine this with the flex-box to get an even more satisfying result.