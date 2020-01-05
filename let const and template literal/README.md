let
==========
let keyword allows us to provide a block scope to a variable. Before ES6 this was not possible.

Example 
	if(true){
	  let name = 'Ryan';
	}
	console.log(name);

const
===================
const is same as let in the sense that this is also block scope. Where it differs is that it provides the ability to define 
a constant value which cannot be changed.

Example
	const age ='20';
	console.log(age);

	age = '40';
	console.log(age);

template literals
============================
- Gives added benefit to define Strings in multi lines
- Helps in easy concatenation of Strings

Example 1
	let firstName = 'Ryan';
	let lastName = 'Christi';

	console.log(`My name is ${firstName}  ${lastName}`)
	
Example 2
	let person = {
	  firstName  'Ryan',
	  lastName  'Max',
	  sayName(){
		return `My name is ${this.firstName}  ${this.lastName}`;
	  }
	}

	console.log(person.sayName());