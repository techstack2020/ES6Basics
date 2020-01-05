Rest Parameters
==================

This is used within a function argument. It converts a list of values to an array.

Example 1:

	let sumUp = function(...args){
	  let result = 0;
	  for(let i =0; i < args.length; i++){
		result += args[i];    
	  }
	  return result;
	}
	console.log(sumUp(8, 9, 10, 2));

Example 2:

	let sum = function(...args) {
		return args.reduce((prev, curr) =>{
		  return prev + curr;
		});
	}
	console.log(sum(8, 9, 10, 2));
	
Example 3:

	let multiply = function(mul, ...args){
	  return args.map(n => mul * n);
	}
	console.log(multiply(2,5,8,7));
	
	
Spread Operator
================

This is reverse of rest parameters and is used when calling a function and is used as an operator.
It allows to pass an array to a method accepting a list of values.

Example 1 :

	let numbers = [2,5,6];
	let maxValue = Math.max(...numbers);
	console.log(maxValue);

Example 2:

	let numbers = [2,5,6];
	let newNumbers = [8,9,...numbers,10];
	console.log(newNumbers);