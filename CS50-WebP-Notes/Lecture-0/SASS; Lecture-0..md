- So far, we’ve found a few ways to eliminate redundancy in CSS such as moving it to separate files or using bootstrap, but there are still quite a few places where we can still make improvements. For example, what if we want several elements to have different styles, but for all of them to be the same color? If we decide later we want to change the color, then we would have to change it within several different elements.
- [Sass](https://sass-lang.com/) is a language that allows us to write CSS more efficiently in several ways, one of which is by allowing us to have variables, as in the following example.
- When writing in Sass, we create a new file with the extension `filename.scss`. In this file, we can create a new variable by adding a `$` before a name, then a colon, then a value. For example, we would write `$color: red` to set the variable color to the value red. We then access that variable using `$color`.
- Here’s an example of our variables.scss file:
```css
$color: red;

ul {
    font-size: 14px;
    color: $color;
}

ol {
    font-size: 18px;
    color: $color;
}
```

* Now, in order to link this styling to our HTML file, we can’t just link to the `.scss` file because most web browsers only recognize `.css` files. To deal with this problem, we have to [download a program called Sass](https://sass-lang.com/install) onto our computers. Then, in our terminal, we write `sass variables.scss:variables.css` This command will compile a .scss file named `variables.scss` into a .css file named `variables.css`, to which you can add a link in your HTML page.
- To speed up this process, we can use the command `sass --watch variables.scss:variables.css` which automatically changes the `.css` file every time a change is detected in the `.scss` file.
- While using Sass, we can also physically nest our styling rather than use the CSS selectors we talked about earlier. For example, if we want to apply some styling only to paragraphs and unordered lists within a div, we can write the following:
```css
div {
    font-size: 18px;

    p {
        color: blue;
    }

    ul {
        color: green;
    }
}
```
Once compiled into CSS, we would get a file that looks like:

```css
div {
    font-size: 18px;
}

div p {
    color: blue;
}

div ul {
    color: green;
}
```

* One more feature that Sass gives us is known as [inheritance](https://sass-lang.com/guide). This allows us to create a basic set of styling that can be shared by several different elements. We do this by adding a `%` before a name of a class, adding some styling, and then later adding the line `@extend %classname` to the beginning of some styling. For example, the following code applies the styling within the `message` class to each of the different classes below, resulting in a webpage that looks like the one below.
```css
%message {
    font-family: sans-serif;
    font-size: 18px;
    font-weight: bold;
    border: 1px solid black;
    padding: 20px;
    margin: 20px;
}

.success {
    @extend %message;
    background-color: green;
}

.warning {
    @extend %message;
    background-color: orange;
}

.error {
    @extend %message;
    background-color: red;
}
```

This looks like this finally :
![[Pasted image 20230830120803.png]]