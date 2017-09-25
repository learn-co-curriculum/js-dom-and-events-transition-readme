# Transition

## Objectives

Congratulations, you've made it over halfway through the JavaScript curriculum! That's awesome. _You're_ awesome.

<picture>
  <source srcset="https://curriculum-content.s3.amazonaws.com/web-development/js/dom-and-events/transition-readme/awesome.webp" type="image/webp">
  <source srcset="https://curriculum-content.s3.amazonaws.com/web-development/js/dom-and-events/transition-readme/awesome.gif" type="image/gif">
  <img src="https://curriculum-content.s3.amazonaws.com/web-development/js/dom-and-events/transition-readme/awesome.gif" alt="Awesome.">
</picture>

You stand now at a precipice. Behind you lie the shiny, new, post-ES2015 lessons. Before you lie ye olde ES5 lessons for the few remaining units in the JavaScript curriculum.

We're working as quickly as we can to update these remaining lessons and reconcile the two bodies of work, but, in the mean time, there are a few key differences for you to be aware of.

## Code style
The code in upcoming lessons is going to lean much more on ES5 than the preceding material did. That means you'll probably see a lot of... **shudder**... `var`, among other things. Don't let this put a dent in the good habits you've cultivated up to this point.

In fact, you can use this older material as a learning experience: see how the code is written with `var`, and then try replacing it with `const` and `let`. What sort of concessions does `var` require that we don't need to worry about with our ES2015 declarations? Can we make the code tighter and more expressive than is possible with the generic `var`?

It's also good practice for seeing code in the real world, much of which still relies on `var` and other pre-ES2015 constructs.

## Testing in Node
The primary difference between the material before and after this point is the way in which it is tested. The preceding labs use our new method for testing JavaScript code: a hot-reloading server that runs the test suite in your browser. While testing in the browser is possible with some of the old labs, the results from those in-browser tests won't get reported to the learn.co servers. To trigger the green light for passing local tests, you must still run the `learn` command in your terminal. On these later labs, instead of starting a hot-reloading test server, the `learn` command will initiate a Node-based Mocha test runner that runs the test suite in your terminal.

We've mentioned Node.js before, but, to briefly recap, it's a JavaScript runtime that allows for running JavaScript code on the server. At its core is V8, the JavaScript engine developed by Google that powers Chrome, among other things. Because Node relies on the same engine that we've been using all along, almost all of the behavior should be consistent. However, there are some slight differences that you should be aware of.

In Node, every separate JavaScript file creates its own scope. That's not a huge deal if you're only writing code in a single file, but it's pretty impactful for our curriculum. If you think about it, every lab we've worked on to this point has consisted of a series of JavaScript files. There's the file you write your solution code in (typically `index.js`); the file that contains the test suite (typically `indexTest.js`); and then the helper libraries that live in the `node_modules/` directory and form the foundation of everything we do. When we test in the browser, we load the various JavaScript files by including them via HTML `<script>` tags in `index.html`. The order in which they're loaded matters because every loaded file is affecting the same global JavaScript environment. If we declare a variable with `const` in the global scope in one file and then reference it in a later file, everything should work fine. The earlier file declared the variable in the same scope (the global scope) that the later file then runs in and has access to.

However, this is not how it works in Node. Because each file creates its own scope, that variable declared with `const` **does not get added to any sort of global Node scope**. If the test suite needs to check for the presence or contents of a variable declared in a separate file (such as `index.js`), declaring the variable with `const` or `let` would prevent the test suite from seeing it. Because of that, it's often impossible to use `const` and `let` in your solutions for these Node-based labs.

### Reading test results
For the most part, you should see the same error messages in the terminal that you would've encountered in the browser. To use `debugger` statements to debug your code, simply insert the `debugger` as you would normally but then run the file with one of the following commands:
- For [Node version 6.x (LTS)](https://nodejs.org/docs/latest-v6.x/api/debugger.html): `node debug <fileName.js>`
- For [Node version 8.x (stable)](https://nodejs.org/docs/latest-v8.x/api/debugger.html): `node inspect <fileName.js>`

To check which version of Node you have, run `node -v` in your terminal.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/js-dom-and-events-transition-readme' title='Transition'>Transition</a> on Learn.co and start learning to code for free.</p>
