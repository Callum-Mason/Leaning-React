# Into to JSX

## Hello World

Take a look at the following line of code:

```jsx
 const h1 = <h1>Hello world</h1>;
 ```

What kind of weird hybrid code is that? Is it JavaScript? HTML? Or something else?

It seems like it must be JavaScript, since it starts with const and ends with ;. If you tried to run that in an HTML file, it wouldn’t work.

However, the code also contains `<h1>Hello world</h1>`, which looks exactly like HTML. That part wouldn’t work if you tried to run it in a JavaScript file.

What’s going on?

### Instructions - app1.js

1. Copy the following line into app.js `const h1 = <h1>Hello world</h1>;`

## The Mystery, Revealed

Good!

Take another look at the line of code that you wrote.

Does this code belong in a JavaScript file, an HTML file, or somewhere else?

The answer is…a JavaScript file! Despite what it looks like, your code doesn’t actually contain any HTML at all.

The part that looks like HTML, `<h1>Hello world</h1>`, is something called JSX.

## What is JSX?

JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

What does “syntax extension” mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can’t read it!

If a JavaScript file contains JSX code, then that file will have to be compiled. That means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.

Codecademy’s servers already have a JSX compiler installed, so you don’t have to worry about that for now. Eventually we’ll walk through how to set up a JSX compiler on your personal computer.

## JSX Elements

A basic unit of JSX is called a JSX element.

Here’s an example of a JSX element:

```jsx
<h1>Hello world</h1>
```

This JSX element looks exactly like HTML! The only noticeable difference is that you would find it in a JavaScript file, instead of in an HTML file.

### Instructions app2.js

1. In app.js, write a JSX `<p></p>` element containing the text, Hello world. Use the example code above as a guide.

## JSX Elements And Their Surroundings

JSX elements are treated as JavaScript expressions. They can go anywhere that JavaScript expressions can go.

That means that a JSX element can be saved in a variable, passed to a function, stored in an object or array…you name it.

Here’s an example of a JSX element being saved in a variable:

```jsx
const navBar = <nav>I am a nav bar</nav>;
```

Here’s an example of several JSX elements being stored in an object:

```jsx
const myTeam = {
  center: <li>Benzo Walli</li>,
  powerForward: <li>Rasha Loa</li>,
  smallForward: <li>Tayshaun Dasmoto</li>,
  shootingGuard: <li>Colmar Cumberbatch</li>,
  pointGuard: <li>Femi Billon</li>
};
```

### Instructions app3.js

1. Create a JSX `<article></article>` element. Save it in a variable named myArticle.

## Attributes In JSX
JSX elements can have attributes, just like HTML elements can.

A JSX attribute is written using HTML-like syntax: a name, followed by an equals sign, followed by a value. The value should be wrapped in quotes, like this:

```jsx
my-attribute-name="my-attribute-value"
```

Here are some JSX elements with attributes:

```jsx
<a href='http://www.example.com'>Welcome to the Web</a>;

const title = <h1 id='title'>Introduction to React.js: Part I</h1>; 
 ```

A single JSX element can have many attributes, just like in HTML:

```jsx
const panda = <img src='images/panda.jpg' alt='panda' width='500px' height='500px' />;
```

### Instructions app4.js

1. Declare a constant named p1.
   Set `p1` equal to a JSX `<p></p>` element. Write the word foo in between the `<p></p>` tags.

2. On the next line, declare a constant named p2.
   Set `p2` equal to another JSX `<p></p>` element. Write the word bar in between the `<p></p>` tags.

3. Give the first `<p></p>` an id attribute of `'large'`.
   Give the second `<p></p>` an id attribute of `'small'`.

## Nested JSX

You can nest JSX elements inside of other JSX elements, just like in HTML.

Here’s an example of a JSX `<h1>` element, nested inside of a JSX `<a>` element:

```jsx
<a href="https://www.example.com"><h1>Click me!</h1></a>
```

To make this more readable, you can use HTML-style line breaks and indentation:

```jsx
<a href="https://www.example.com">
  <h1>
    Click me!
  </h1>
</a>
```

If a JSX expression takes up more than one line, then you must wrap the multi-line JSX expression in parentheses. This looks strange at first, but you get used to it:

```jsx
(
  <a href="https://www.example.com">
    <h1>
      Click me!
    </h1>
  </a>
)
```

Nested JSX expressions can be saved as variables, passed to functions, etc., just like non-nested JSX expressions can! Here’s an example of a nested JSX expression being saved as a variable:

```jsx
 const theExample = (
   <a href="https://www.example.com">
     <h1>
       Click me!
     </h1>
   </a>
 );
```

### Instructions app5.js

1. Declare a new variable named myDiv. Set myDiv equal to a JSX `<div></div>` element.
   Wrap the `<div></div>` in parentheses, and use indentation and line breaks like in the examples. In between the `<div></div>` tags, nest an `<h1></h1>` containing the text Hello world.

## JSX Outer Elements

There’s a rule that we haven’t mentioned: a JSX expression must have exactly one outermost element.

In other words, this code will work:

```jsx
const paragraphs = (
  <div id="i-am-the-outermost-element">
    <p>I am a paragraph.</p>
    <p>I, too, am a paragraph.</p>
  </div>
);
```

But this code will not work:

```jsx
const paragraphs = (
  <p>I am a paragraph.</p> 
  <p>I, too, am a paragraph.</p>
);
```

The first opening tag and the final closing tag of a JSX expression must belong to the same JSX element!

It’s easy to forget about this rule, and end up with errors that are tough to diagnose.

If you notice that a JSX expression has multiple outer elements, the solution is usually simple: wrap the JSX expression in a `<div></div>`.

### Instructions app6.js

1. Your friend’s blog is down! He’s asked you to fix it.
   You immediately diagnose the problem: a JSX expression with multiple outer elements.
   Repair your friend’s broken code by wrapping their JSX in a `<div></div>`.
