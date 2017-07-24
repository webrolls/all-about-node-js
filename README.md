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
</pre>


HOW DOES MODULES IN NODE WORKS ?????

when we use require node method what actually happens ??? this is the reason why the function and variable in required files are not available in global scope. 

<pre>
var greet = require('./greet.js');
</pre>
1- wraps the containt of the file in

<pre>
(function(exports, require, module, __filenmae, __dirname) {
});
</pre>
2- run the code using . apply(params...)

<pre>
fn(module.exports, require, module, filename, dirname);
</pre>
3- return the module.exports;
<pre>
return module.exports;
</pre>

Note: 
when we requires a file in nodejs and that file does not exist nodejs will look for the folder with same name and pickup index.js in that folder.

do exmaple 


// Greet 01
module.exports = function() {
	console.log('Hello world');
};

// Greet 02
module.exports.greet = function() {
	console.log('Hello world!');
};


// Greet 03
function Greetr() {
	this.greeting = 'Hello world!!';
	this.greet = function() {
		console.log(this.greeting);
	}
}

module.exports = new Greetr();


// Greet 04
function Greetr() {
	this.greeting = 'Hello world!!!';
	this.greet = function() {
		console.log(this.greeting);
	}
}

module.exports = Greetr;


// Greet 05
var greeting = 'Hello world!!!!';

function greet() {
	console.log(greeting);
}

module.exports = {
	greet: greet
}


app.js

<pre>
var greet = require('./greet1');
greet();

var greet2 = require('./greet2').greet;
greet2();

var greet3 = require('./greet3');
greet3.greet();
greet3.greeting = 'Changed hello world!';

var greet3b = require('./greet3');
greet3b.greet();

var Greet4 = require('./greet4');
var grtr = new Greet4();
grtr.greet();

var greet5 = require('./greet5').greet;
greet5();
</pre>



