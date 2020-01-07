Modules
==================

Even though JavaScript never had built-in modules, the community has converged on a simple style of modules, which is supported by libraries in ES5 and earlier. This style has also been adopted by ES6:

	* Each module is a piece of code that is executed once it is loaded. 
	* In that code, there may be declarations (variable declarations, function declarations, etc.).
		* By default, these declarations stay local to the module. 
		* You can mark some of them as exports, then other modules can import them.
	* A module can import things from other modules. It refers to those modules via module specifiers, strings that are either:
		* Relative paths ('../model/user'): these paths are interpreted relatively to the location of the importing module. The file extension .js can usually be omitted.
		* Absolute paths ('/lib/js/helpers'): point directly to the file of the module to be imported.
		* Names ('util'): What modules names refer to has to be configured.
	* Modules are singletons. Even if a module is imported multiple times, only a single “instance” of it exists.
	
Example 1:

	external.js
	--------------------
	
	export let myVariable = 1000;
	export function addition(a, b){
		return a-b;
	}
	export default function(text){
		console.log(`Modules are ${text}`);
	}
	
	app.js
	---------------------
	import myFunction from './external.js';
	import {myVariable} from './external.js';
	import {addition} from './external.js';

	myFunction('Neat');
	console.log(myVariable);
	console.log(addition(35, 25));
	
Example : 2

	external.js
	--------------------
	let myVariable = 1000;

	function addition(a, b){
		return a-b;
	}

	export {myVariable, addition}; 	// Grouping of exports

	export default function(text){
		console.log(`Modules are ${text}`);
	}

	app.js
	---------------------
	import myFunction from './external.js';
	import {myVariable, addition} from './external.js';		// Grouping of imports

	myFunction('Neat');
	console.log(myVariable);
	console.log(addition(35, 25));