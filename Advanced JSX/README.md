# ADVANCED JSX

## class vs className

This lesson will cover more advanced JSX. You’ll learn some powerful tricks, and some common errors to avoid.

Grammar in JSX is mostly the same as in HTML, but there are subtle differences to watch out for. Probably the most frequent of these involves the word `class`.

In HTML, it’s common to use `class` as an attribute name:

```jsx
<h1 class="big">Hey</h1>
In JSX, you can’t use the word class! You have to use className instead:

<h1 className="big">Hey</h1>
```

This is because JSX gets translated into JavaScript, and class is a reserved word in JavaScript.

When JSX is rendered, JSX className attributes are automatically rendered as class attributes.

### Instructions app1.jsx

1. On line 5, declare a new variable named myDiv. Set myDiv equal to a JSX `<div></div>` element.
   In between the `<div></div>` tags, write the text `I AM A BIG DIV`.
   Give your `<div></div>` the following attribute:

   ```jsx
   className="big"
   ```

2. Underneath your `<div></div>`, call ReactDOM.render.
   For `ReactDOM.render()`‘s first argument, pass in myDiv.
   For ReactDOM.render()‘s second argument, pass in document`.getElementById('app')`.
   If your rendered `<div></div>` has a class of "big", then it should look big in the browser!

## Self-Closing Tags

Another JSX ‘gotcha’ involves self-closing tags.

What’s a self-closing tag?

Most HTML elements use two tags: an opening tag (`<div>`), and a closing tag (`</div>`). However, some HTML elements such as `<img>` and `<input>` use only one tag. The tag that belongs to a single-tag element isn’t an opening tag nor a closing tag; it’s a self-closing tag.

When you write a self-closing tag in HTML, it is optional to include a forward-slash immediately before the final angle-bracket:

```html
Fine in HTML with a slash:
 
  <br />
 
Also fine, without the slash:
 
  <br>
```

But!

In JSX, you have to include the slash. If you write a self-closing tag in JSX and forget the slash, you will raise an error:

```jsx
//Fine in JSX:
 
  <br />
 
//NOT FINE AT ALL in JSX:
 
  <br>
```

### Instructions app2.jsx

1. In app2.jsx, fix the broken JSX by adding slashes to all of the self-closing tags.

## JavaScript In Your JSX In Your JavaScript

So far, we’ve focused on writing JSX expressions. It’s similar to writing bits of HTML, but inside of a JavaScript file.

In this lesson, we’re going to add something new: regular JavaScript, written inside of a JSX expression, written inside of a JavaScript file.

Whoaaaa…

### Instructions app3.jsx

1. Starting on line 5, carefully write the following code. What do you think will appear in the browser?

   ```jsx
   ReactDOM.render(
        <h1>2 + 3</h1>,
        document.getElementById('app')
    );
    ```

## Curly Braces in JSX

The code in the last exercise didn’t behave as one might expect. Instead of adding 2 and 3, it printed out “2 + 3” as a string of text. Why?

This happened because `2 + 3` is located in between `<h1>` and `</h1>` tags.

Any code in between the tags of a JSX element will be read as JSX, not as regular JavaScript! JSX doesn’t add numbers - it reads them as text, just like HTML.

You need a way to write code that says, “Even though I am located in between JSX tags, treat me like ordinary JavaScript and not like JSX.”

You can do this by wrapping your code in curly braces.

### Instructions app4.jsx

1. Add a pair of curly braces to the code from last exercise, so that your JSX expression looks like this:

    ```jsx
    <h1>{2 + 3}</h1>
    ```

    Everything inside of the curly braces will be treated as regular JavaScript.

## 20 Digits of Pi in JSX

You can now inject regular JavaScript into JSX expressions! This will be extremely useful.

In the code editor, you can see a JSX expression that displays the first twenty digits of pi.

Study the expression and notice the following:

* The code is written in a JavaScript file. By default, it will all be treated as regular JavaScript.
* Find `<div>` on line 5. From there up through `</div>`, the code will be treated as JSX.
* Find `Math`. From there up through `(20)`, the code will be treated as regular JavaScript again.
* The curly braces themselves won’t be treated as JSX nor as JavaScript. They are markers that signal the beginning and end of a JavaScript injection into JSX, similar to the quotation marks that signal the boundaries of a string.

### Instructions app5.jsx & pi5.jsx

1. Select app5.jsx.
    Declare a new variable named math. Set math equal to a JSX `<h1></h1>` element.
    Put the following text inside of the `<h1>`:

    ```jsx
    2 + 3 = 2 + 3
    ```

2. At the bottom of the file, call `ReactDOM.render()`.
    For `ReactDOM.render()`‘s first argument, pass in math.
    For `ReactDOM.render()`‘s second argument, pass in `document.getElementById('app')`.

3. As you probably expected, the equation was displayed as a string.
    Insert a pair of curly braces into the `<h1></h1>`, so that the browser displays 2 + 3 = 5.

## Variables in JSX

When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

That means that you can access variables while inside of a JSX expression, even if those variables were declared on the outside.

```jsx
// Declare a variable:
const name = 'Gerdo';
 
// Access your variable 
// from inside of a JSX expression:
const greeting = <p>Hello, {name}!</p>;
```

### Instructions app6.jsx

1. Replace `ReactDOM.render()`‘s first argument with a JSX `<h1></h1>`.
   Using curly braces, set the `<h1></h1>`‘s inner text equal to `theBestString`.

## Variable Attributes in JSX

When writing JSX, it’s common to use variables to set attributes.

Here’s an example of how that might work:

```jsx
// Use a variable to set the `height` and `width` attributes:
 
const sideLength = "200px";
 
const panda = (
  <img 
    src="images/panda.jpg" 
    alt="panda" 
    height={sideLength} 
    width={sideLength} />
);
```

Notice how in this example, the `<img />`‘s attributes each get their own line. This can make your code more readable if you have a lot of attributes on one element.

Object properties are also often used to set attributes:

```jsx
const pics = {
  panda: "http://bit.ly/1Tqltv5",
  owl: "http://bit.ly/1XGtkM3",
  owlCat: "http://bit.ly/1Upbczi"
}; 
 
const panda = (
  <img 
    src={pics.panda} 
    alt="Lazy Panda" />
);
 
const owl = (
  <img 
    src={pics.owl} 
    alt="Unimpressed Owl" />
);
 
const owlCat = (
  <img 
    src={pics.owlCat} 
    alt="Ghastly Abomination" />
); 
```

### Instructions app7.jsx

1. On line 7, declare a new variable named `gooseImg`. Set its value equal to a JSX `<img />` element.
   Give the `<img />` an attribute with a name of `src`. Set the attribute’s value equal to the variable `goose`.

2. Use `ReactDOM.render()` to render `gooseImg`.
   `ReactDOM.render()`‘s first argument should be `gooseImg`.
   `ReactDOM.render()`‘s second argument should be `document.getElementById('app')`.
