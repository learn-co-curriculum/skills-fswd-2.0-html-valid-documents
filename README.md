# Validation for HTML Documents

## Problem Statement

Let's say you've written some HTML pages, and you're noticing some strange behaviors
in the browser. What is the best way to debug the code without having to meticulously 
comb through dozens of lines of HTML code? What if you have a fancy code editor that 
has syntax highlighting and other features that can catch some syntax errors, but
you're still noticing that you're still having display or performance issues with your
code? Or, maybe you are a perfectionist and want to make sure your HTML is as error-free
as possible! Like all programming languages, we have tools that address these needs.
HTML validation is a great place to start!

## Objectives

1. What are Common Cases Invalid HTML?
2. Why Does Validation Matter?
3. What are Accepted Sources for HTML Validation?

## What are Common Cases Invalid HTML?

In markup languages there are generally two types of errors with code--syntax errors
and logic errors. Syntax errors usually involve a mistake that causes the browser
to be unable to execute the code properly (e.g., missing closing tags or symbols).
Logic errors arise when the code is syntactically correct, but doesn’t do exactly
what it was meant to do.

Many developers are familiar with HTML validation guidelines, but may unintentionally write
invalid code. A valid HTML5 document at its bare minimum must contain the doctype and
title, with a non-whitespace character:

```html 
<!doctype html><title>Some Title or Non-Whitespace character</title>
```

What looks most familiar to many are HTML documents that contain the `html`,
`head`, and `body` tags, optional metadata such as the example below:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello World!</title>
    <meta name="description" content="A Basic HTML Document">
  </head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
```
When working in `iframes` only the bare minimum markup is needed for validation. 

##### Other Invalid HTML Consist of the Following Cases: 
Leaving any tags unclosed or closed in the incorrect order is invalid
markup and result in unpredictable performance and rendering. For example:

```html
<p><a href="#"></strong>Hello World</p>
```

- Opera would make the subsequent elements children of the anchor element.
- Firefox would add extra anchor elements which were not present in the markup.
- Internet Explorer would put "Hello World!" outside the anchor tag that creates
the link.

Most presentational markup/tags from previous versions of HTML are no longer allowed and are 
considered invalid, or have been redefined by the HTML5 documentation. 

```html
<font color="red">Hello World!</font>
```

The `style` attribute and the `style` element replace the previous invalid markup:

```html
<p style="color: red;">Hello World!</p>
```

Syntax errors as noted below can cause unpredictable behavior. 
For example, leaving attributes unclosed, or improperly closed:

```html
<p><a href="/html>Hello World!</a></p>
```
```html
<p><a href="/html'>Hello World!</a></p>
```

Markup that is written in a way that the author's intent is unclear also invalid:

```html
<h1>Hello World!</h2>
```
In this case, the browser would not be able to interpret if it should render an `h1` 
or an `h2` based on this sytax.

Typos in tags and attributes would also be invalid:
```<heder> instead of </header>```

## Why Does Validation Matter?

Why should we validate an HTML document? Sometimes web developers think that if a web page
looks fine in browsers, it doesn’t matter if it doesn’t validate. They describe validation
as an ideal goal, but not something that is a black-and-white issue.

* A valid document is correctly and more consistently displayed by browsers.
* Invalid HTML code can trigger bugs hard to targe.
* A valid document is easier to maintain by all parties.
* Some invalid documents can cause errors that lead to poor website performance. 
* Invalid markup can lead to poorer accessibility.

Developers are not always perfect, and mistakes will be made in the code code. 
Web pages will be higher quality if the mistakes are weeded out. In the future, browsers will
inevitably change. It is likely that browsers will be less, not more, forgiving when parsing
invalid code.


## What are Accepted Sources for HTML Validation?

The best way to debug, even when your page may seem to display properly, and to ensure
that these and future pages will be displayed properly across browsers, with no errors
is to validate! The most common validators you’ll use are:

* [Validator.nu](https://html5.validator.nu/): A new-school validator that validates HTML5,
ARIA, SVG 1.1 and MathML 2.0, it checks the entire document pointing out places where your
markup doesn’t follow that doctype correctly (i.e., where there are errors). This is the
one we recommend if you are using the HTML5 doctype, also highly recommended. 

* [The W3C MarkUp Validator](https://validator.w3.org/): This looks at the (X)HTML doctype
for the document you want to check, and then validates your markup accordingly. This is
the one we recommend if you are using an HTML4 or XHTML1.x doctype. It does validate HTML5,
but validator.nu is arguably more up to date.

* [The W3C Link Checker](https://validator.w3.org/checklink): This checks a document, and
tests all the links to make sure they are not broken (e.g., that the `<href>` values point
to resources that actually exist).

* [The W3C CSS Validator](https://jigsaw.w3.org/css-validator/): This checks a CSS (or HTML/CSS)
document and verifies that the CSS follows the specs properly.

In order to validate put the URL or copy and paste the markup into a validator and address and
use the error messages to debug and clean up your code.

## Conclusion

When coding, it can be easy to make mistakes. Even when the document looks visually correct
in one or more browsers, it's important to understand that invalid code can have more impact
on the web pages than visual elements. It can create performance issues--if not now, then 
potentially in the future. Using HTML validators to cleanup as many issues as possible can
improve website performance and stability.

## Resources

* [Invalid Markup Examples](https://www.w3.org/2005/Talks/0908-wcag/Table_7b.html)
* [HTML Validation](https://webplatform.github.io/docs/guides/html_validation/)