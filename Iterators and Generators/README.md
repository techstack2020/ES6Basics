# Iterators and Generators

## Iterators

An iterator is an object that can access one item at a time from a collection while keeping track of its current position.
Basically an iterator has a function – next() – which allows you to output values step by step.

	let arrayObj = [1,2,3];
	let iterator = arrayObj[Symbol.iterator](); // returns an iterator object
	console.log(iterator.next());
	console.log(iterator.next());
	console.log(iterator.next());
	console.log(iterator.next());

### Iterables in JavaScript

A lot of things are iterables in JavaScript. It may not be visible immediately, but if you examine closely, iterables will start to show.
These are all iterables :

	* Arrays and TypedArrays
	* Strings — iterate over each character or Unicode code-points.
	* Maps — iterates over its key-value pairs
	* Sets — iterates over their elements
	* arguments — An array-like special variable in functions
	* DOM elements (Work in Progress)
	
### Custom Iterable Object

	let person = {
	  name : 'Max',
	  hobbies : ['running', 'swimming', 'jogging'],
	  [Symbol.iterator] : function() {
		let i = 0;
		let hobbies = this.hobbies;
		return{
		  next : function(){
			let values = hobbies[i];
			i++;
			return {
			  done : i > hobbies.length ? true :false,
			  value : values
			};
		  }
		};
	  }
	};

	for(element of person){
	  console.log(element);
	}
	
	let iterator = person[Symbol.iterator]();
	console.log(iterator.next());
	
## Generators

Generators are functions which don’t necessarily run to the end upon execution. Instead, upon each call they yield a value.
A generator is created by adding an asterisk in front of the function name.

	function *select() {
	 yield 'House Data';
	 yield 'Person Data';
	}

When executing a function they don’t return a value immediately, instead an iterator is returned. 
This iterator may then be used to access the returned values step by step.

	let iterator = select();
	console.log(iterator.next()); // prints House Data
	console.log(iterator.next()); // prints Person Data
	console.log(iterator.next()); // prints undefined
	
Of course you may also pass arguments to generators and use them in the function body.