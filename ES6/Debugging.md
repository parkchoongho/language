# Debugging

Debugging is a valuable and (unfortunately) necessary tool for programmers. It follows the testing phase of checking if your code works as intended, and discovering it does not. Debugging is the process of finding exactly what isn't working and fixing it. After spending time creating a brilliant block of code, it is tough realizing it may have errors. These issues generally come in three forms: 1) syntax errors that prevent a program from running, 2) runtime errors when code fails to execute or has unexpected behavior, and 3) semantic (or logical) errors when code doesn't do what it's meant to.

Modern code editors (and experience) can help identify syntax errors. Semantic and runtime errors are harder to find. They may cause your program to crash, make it run forever, or give incorrect output. Think of debugging as trying to understand why your code is behaving the way it is.

Example of a syntax error - often detected by the code editor:



> funtion willNotWork( {
>   console.log("Yuck");
> }
> // "function" keyword is misspelled and there's a missing parenthesis



> function loopy() {
>   while(true) {
>     console.log("Hello, world!");
>   }
> }
> // Calling loopy starts an infinite loop, which may crash your browser



> function calcAreaOfRect(w, h) {
>   return w + h; // This should be w * h
> }
> let myRectArea = calcAreaOfRect(2, 3);
> // Correct syntax and the program executes, but this gives the wrong answer



Debugging is frustrating, but it helps to develop (and follow) a step-by-step approach to review your code. This means checking the intermediate values and types of variables to see if they are what they should be. You can start with a simple process of elimination.
For example, if function A works and returns what it's supposed to, then function B may have the issue. Or start checking values in a block of code from the middle to try to cut the search space in half. A problem in one spot indicates a bug in the first half of the code. If not, it's likely in the second.

<br>

<br>

### Use the JavaScript Console to Check the Value of a Variable

Both Chrome and Firefox have excellent JavaScript consoles, also known as DevTools, for debugging your JavaScript.

You can find Developer tools in your Chrome's menu or Web Console in FireFox's menu. If you're using a different browser, or a mobile phone, we strongly recommend switching to desktop Firefox or Chrome.

The `console.log()`method, which "prints" the output of what's within its parentheses to the console, will likely be the most helpful debugging tool. Placing it at strategic points in your code can show you the intermediate values of variables. It's good practice to have an idea of what the output should be before looking at what it is. Having check points to see the status of your calculations throughout your code will help narrow down where the problem is.

Here's an example to print 'Hello world!' to the console:

```javascript
console.log('Hello world!');
```