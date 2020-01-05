Arrow Functions
=================

This is similar to Lambdas in Java. Only diference is that instead of -> it uses => (double arrow)

Examples 1: (Single line arrow function)
	
	let add = (a, b) => a + b;
	console.log(add(10,20));
	
Example 2: (Multi line arrow function with curly braces)
	
	let add = (a, b) => {
	  console.log(a + b);
	}

	add(20,40);
Example 3: 

	let numbers = [10,20,30,40,50];
	let doubledNumbers = numbers.map(numbers => numbers * 2);
	console.log(doubledNumbers);
	
In case of arrow functions the 'this' keyword has a lexical scope (or something like a parent scope)

Example 4:
	// This wont work
	let person = {
		name : 'Ryan',
		sayHello : () => {
			console.log(`Say hello to ${this.name}`);
		}
	}
	person.sayHello();
	
	// This will work
	let person = {
	  name : 'Ryan',
	  sayHello : function()  {
		console.log(`Say hello to ${this.name}`);
	  }
	}
	person.sayHello();
	

