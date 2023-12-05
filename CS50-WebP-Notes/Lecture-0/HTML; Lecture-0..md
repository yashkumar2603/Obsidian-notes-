1. **HTML and CSS** (a markup language used to outline a webpage, and a procedure for making our sites more visually appealing)
2. **Git** (used for version control and collaboration)
3. **Python** (a widely-used programming language we’ll use to make our sites more dynamic)
4. **Django** (a popular web framework we’ll use for the backend of our sites)
5. **SQL, Models, and Migrations** (a language used for storing and retrieving data, and Django-specific methods that make it easier to interact with SQL databases)
6. **JavaScript** (a programming language used to make websites faster and more interactive)
7. **User Interfaces** (methods used to make a website as easy to use as possible)
8. **Testing, CI, CD** (learning about different methods used to make sure updates to web pages proceed smoothly)
9. **Scalability and Security** (making sure our websites can be accessed by many users at once, and that they are safe from malicious intent)

### Basic HTML :
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Hello!</title>
    </head>
    <body>
        Hello, world!
    </body>
<html>
```

the following code does this - 
- In the first line, we are declaring (to the web browser) that we are writing the document in the latest version of HTML: HTML5.
- After that, the page consists of nested **HTML elements** (such as html and body), each with an **opening and closing tag** marked with either `<element>` for an opening and `</element>` for a closing.
- Notice how each of the inner elements is indented just a bit further than the last. While this is not necessarily required by the browser, it will be very helpful to keep this up in your own code.
- HTML elements can include **attributes**, which give the browser extra information about the element. For example, when we include `lang="en"` in our initial tag, we are telling the browser that we are using English as our primary language.
- Inside the HTML element, we typically want to include both a `head` and a `body` tag. The head element will include information about your page that is not necessarily displayed, and the body element will contain what is actually visible to users who visit the site.
- Within the head, we have included a `title` for our webpage, which you’ll notice is displayed in the tab at the top of our web browser.
- Finally, we’ve included the text “Hello, world!” in the body, which is the visible part of our page.

### Document Object Model (DOM) : 
![[Pasted image 20230829163509.png]]

### More Tags and elements in HTML :

##### Don't memorise them, just look up to whatever u need on 
[HTML Elements (w3schools.com)](https://www.w3schools.com/html/html_elements.asp)

One more thing to note: `<!-- -->` gives us a comment in HTML, so we’ll use that below to explain some of the elements

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>HTML Elements</title>
</head>

<body>
    <!-- We can create headings using h1 through h6 as tags. ->
    <h1>A Large Heading</h1>
    <h2>A Smaller Heading</h2>
    <h6>The Smallest Heading</h6>

    <!-- The strong and i tags give us bold and italics respectively. -->
    A <strong>bold</strong> word and an <i>italicized</i> word!

    <!-- We can link to another page (such as cs50's page) using a. -->
    View the <a href="https://cs50.harvard.edu/">CS50 Website</a>!

    <!-- We used ul for an unordered list and ol for an ordered one. both ordered and unordered lists contain li, or list items. -->
    An unordered list:
    <ul>
        <li>foo</li>
        <li>bar</li>
        <li>baz</li>
    </ul>
    An ordered list:
    <ol>
        <li>foo</li>
        <li>bar</li>
        <li>baz</li>
    </ol>
  
    <!-- Images require a src attribute, which can be either the path to a file on your computer or the link to an image online. It also includes an alt attribute, which gives a description in case the image can't be loaded. -->
    An image:
    <img src="../../images/duck.jpeg" alt="Rubber Duck Picture">
    <!-- We can also see above that for some elements that don't contain other ones, closing tags are not necessary. -->
  
    <!-- Here, we use a br tag to add white space to the page. -->
    <br /> <br />
  
    <!-- A few different tags are necessary to create a table. -->
    <table>
        <thead>
            <th>Ocean</th>
            <th>Average Depth</th>
            <th>Maximum Depth</th>
        </thead>
        <tbody>
            <tr>
                <td>Pacific</td>
                <td>4280 m</td>
                <td>10911 m</td>
            </tr>
            <tr>
                <td>Atlantic</td>
                <td>3646 m</td>
                <td>8486 m</td>
            </tr>
        </tbody>
    </table>
</body>
<html>
```

### HTML Forms :

- Another set of elements that is really important when creating a website is how to collect information from users. You can allow users to enter information using an HTML form, which can contain several different types of input. Later in the course, we’ll learn about how to handle information once a form has been submitted.
- Just as with other HTML elements, there’s no need to memorize these, and W3 Schools is a great resource for learning about them!

```html
<body>
    <form>
        <input type="text" placeholder="First Name" name="first">
        <input type="password" placeholder="Password" name="password">
        <div>
            Favorite Color:
            <input 
	            name="color" 
	            type="radio" 
	            value="blue"> Blue
            <input 
	            name="color" 
	            type="radio" 
	            value="green">Green
            <input 
	            name="color" 
	            type="radio" 
	            value="yellow">Yellow
            <input 
	            name="color" 
	            type="radio" 
	            value="red"> Red
        </div>
        <input type="submit">
    </form>
</body>
```

In this `<input>` tag, 
* the type is the type of method for giving the input, the radio signifies a button click, for a checkbox system.
* the name is the name with which the form comes to the form owner or collector as the field. The name='password', allows us to hide the password while typing. Automatically.
* the value is what is displayed on the screen.
* the placeholder is the text in the text box before we start typing.
* the input type submit, creates a button with submit written in it, which allows us to submit the form.

##### A newer variation in the input tags is :
```html
<label for="browser">Choose your browser from the list:</label>  
<input list="browsers" name="browser" id="browser">  
  
<datalist id="browsers">  
  <option value="Edge">  
  <option value="Firefox">  
  <option value="Chrome">  
  <option value="Opera">  
  <option value="Safari">  
</datalist>
```

This creates a dropdown selector like this:
![[Pasted image 20230829165315.png]]
Also we can type what we want and it will be searched automatically.  

Now, these are just the structures of a webpage, to make a webpage elegant and pleasing we use CSS.
[[CSS; Lecture-0.]]



