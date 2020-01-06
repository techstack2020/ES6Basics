Destructuring
================

Destructuring is a way to extract data from different data structures. It is new to ES6.

Example 1:

	let person = {
	  name : 'Ryan',
	  age : 28,
	  location : 'Bangalore'
	}

	console.log(person.age);
	console.log(person["age"]);

	let {age : personAge} = person;
	console.log(personAge);

	let {name} = person;
	console.log(name);

	let {name : fname, location: myLocation} = person;
	console.log(fname, myLocation);
	
Example : 2 (Using arrays)

	let numbers = [1,2,3,4];
	let [first,second] = numbers;
	console.log(first,second);
	let [firstNum,,,fourthNum] = numbers;
	console.log(fourthNum);
	
#Example where this is used in real world is react.js

	import { Route, Link, BrowserRouter as Router } from 'react-router-dom'