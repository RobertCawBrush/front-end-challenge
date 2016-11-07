<h1> Front End Challange </h1>

<h2> Foreword</h2>

If you want to see the code in ES5 look into the `bundle.js`, This code is generated so I'm not completely sure how it looks. For my intended code look at the `script.js`. There is no need to run webpack as I made sure to commit my bundled code. Everything works as normal just start MAMP then navigate to the index file.

There are a couple of commits I made over the weekend to the index as I was using local dependencies and didn't want to force an `npm install` on a project that had defined plans on what you would do when reviewing.

<h2>Formatting</h2>

An IIFE was wrapped around the entire script to avoid variable leakage

A `'use strict';` was placed at the top of the document to force the code conventions we want to follow to avoid careless errors

All lines of code that should be terminated are terminated with ;, not doing this and leaving it up to the compiler to add ; can cause silent errors

All == signs were changed to === to avoid coercian( or what is known as a type of typeCasting) which if left by itself an if statement like `if(1 == '1')`` will evaluate
true

All variables were changed to be defined as explicit variables

All variables were camelCased and all constructors were pascal cased as per modern conventions

From there I reformatted a good amount of the whitespace to be much much easier to read
(there was an area of code that was formatted like you would see a config, I changed that but that was a matter of preference

<h2>Understanding the code</h2>

`ah geez, it's ALL jQuery`

The next step was running through the code with a debugger to understand exactly what was happening. Initially, nothing was displaying on the page even after setting up the apache server,
from the readme it looked like this was undesirable and it was supposed to fail something like 6/10 times. My solution (or what was supposed to be the solution) was to introduce promises.

I think promises have been back ported to native ES5 but to make sure I imported ES6 to get them. As ES6 is not a library rather a new iteration of javascript I count it as not violating that rule. With ES6 comes arrows functions, promises, operations that remove the need for for loops, and much more.
Es6 isn't natively supported in all browsers yet so I needed to transpile my code. I installed Webpack and babel and the presets it needed to function. Again these are all just tools there isn't any code provided by
 webpack or babel.

 From what I gather the code works as follows:

 1. An object is created that has functions constructed on it, this first object is necessary mainly for the self.products array

 2. An AJAX call is made from that object and a for loop worker ran to populate self.products which fills said array with fifty something objects

 3. Qith the calls completion page.updateProductHTML is called and it fires another worker that devours the properties on the objects in self.products which psueod binds the values to a template

 4. From there the code runs it's final function, page.updateDOM, which attempts to build the HTML's rows alternating between the remainder of 3 populating a row every 3 elements

 5. If everything executed in order than the page loads with about fifty components

 <h3>What I did improve</h3>

 I reduced the ajax request for the template as it was calling every single time but the code it return didn't need to be mutated

 I refactored the function calls out of timeouts into a promise chain for speed and consistency. I could have also used callbacks.

 Overall the time was reduced from 5000ms to around 1400ms.

 <h3>What I would improve, and libraries</h3>

 This day in age a jQuery only frontEnd is fairly legacy, I would reWrite as soon as you could using something like React/Redux or even Angular.
 The speed you would gain would be worth it alone besides how simple some of the code could be rendered. Frameworks also significantly speed up development time and can cut down on the amount of libraries you are currently using.

 Bootstrap would also be easier to use along with some mixins from SASS/LESS or even SCSS

 I would immediately cease using global variables as they can cause protectedName clashes as well as overwrite prototypes and cause general chaos.
 Generally, variables should be declared locally and passed into functions as needed. Redux handles that pretty well with how it manages State(immutable state).

 Maybe look into ES6 or TypeScript and refactor to a more class based system. From the challenge code, it seems you favor that type of programming.

 I'd install a linter to check that a specific format is kept project wide, and define a specific server for my code(not depending on MAMP). Cleaner code is better code.

 I'd move your AJAX calls to REST based calls.

 To maximize speed, all code needs to be uglified/minified to eliminate white space and long variable names (I noticed some code wasn't minified on ToMos main page). Besides the speed increase the file will also be smaller speeding the runTime up even more.
 
 Something else that I believe needs work is the method I am using for the loading widget. It's not very consistent with appearing and disappearing and seems to have a particular issue with having a cache. While it's very minor i think it could use some work.

  <h2> wrap up</h2>
 The challenge was interesting and I will be recreating the page in React in the next coming days.
