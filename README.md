# all-about-node-js


first=class functions - in js we can treat function as anyother type like assign something value/function, put in array

joyent -> node.js -> v8 -> cpp

<pre>function statment 

function greet() {
console.log('hiiii !');
}

greet() // hiiii !
</pre>

// 1. functions are first-class in js
<pre>
function callFunc(fn) {  
fn();
}

callFunc(greet); // hiiii !
</pre>
// 2. function expression
<pre>
var greetMe2 = function () {
      console.log('Hi from expresssion !! ');
}
greetMe2(); 

callFunc(greetMe2); //Hi from expresssion !!
</pre>

//3.  function express on the fly
<pre>
callFunc(function(){
console.log('hiiii !')
}); 

</pre>

NODE MODULE
1. 

<pre>
app.js
greet.js

app.js
require('./greet.js')

greet.js
function greet() {
console.log('hiiii !');
}
greet() 
</pre>
note: greet function in greet.js will not collid with greet function in app.js else or the greet function will not be avaiable in app.js directly to call like greet(); its a very good feature of nodejs like modularized !

RUN node app.js

2.
if you want to make greet() function from greet.js avaiable in app.js here is what we need to do

<pre>
app.js
var greet = require('./greet')
greet();

greet.js
var greet = function () {
  console.log('Hello!');
}

module.exports = greet;
<pre>
