- It turns out that there are many libraries that other people have already written that can make the styling of a webpage even simpler. One popular library that we’ll use throughout the course is known as **bootstrap**.
- We can include bootstrap in our code by adding a single line to the head of our HTML file:
- `<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">`
- To get the bootstrap components one needs, just go to getbootstrap.com and in the components section, look out for whatever we need. and copy-paste the required snippet.

* One popular bootstrap feature is their [grid system](https://getbootstrap.com/docs/4.0/layout/grid/). Bootstrap automatically splits a page into 12 columns, and we can decide how many columns an element takes up by adding the class `col-x` where `x` is a number between 1 and 12. For example, in the following page, we have a row of columns of equal width, and then a row where the center column is larger:
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>My Web Page!</title>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
        <style>
            .row > div {
                padding: 20px;
                background-color: teal;
                border: 2px solid black;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col-4">
                    This is a section.
                </div>
                <div class="col-4">
                    This is another section.
                </div>
                <div class="col-4">
                    This is a third section.
                </div>
            </div>
        </div>
        <br/>
        <div class="container">
            <div class="row">
                <div class="col-3">
                    This is a section.
                </div>
                <div class="col-6">
                    This is another section.
                </div>
                <div class="col-3">
                    This is a third section.
                </div>
            </div>
        </div>
    </body>
</html>
```

* To get the bootstrap components one needs, just go to getbootstrap.com and in the components section, look out for whatever we need. and copy-paste the required snippet.
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>My Web Page!</title>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
        <style>
            .row > div {
                padding: 20px;
                background-color: teal;
                border: 2px solid black;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col-lg-3 col-sm-6">
                    This is a section.
                </div>
                <div class="col-lg-3 col-sm-6">
                    This is another section.
                </div>
                <div class="col-lg-3 col-sm-6">
                    This is a third section.
                </div>
                <div class="col-lg-3 col-sm-6">
                    This is a fourth section.
                </div>
            </div>
        </div>
    </body>
</html>
```

* The classes `class="col-lg-3 col-sm-6"` and similar, refer to the instruction that, on large screens the div takes up 3 columns, on smaller screens, it should take up 6 columns, and since 4 divs are taking up 6 columns each on the smaller screens, we will get two divs below the other  two.