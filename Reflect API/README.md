# Reflect API

## Metaprogramming

Metaprogramming means that you’re able to change (parts of) the behavior of the underyling language – JavaScript in this case. 
This of course is a powerful feature as it allows you to influence the way your code is executed. 
The Reflect API (like Symbols and Proxies) are important additions which help you with Metaprogramming – something that wasn’t
really possible in JavaScript before.

## What is the Reflect API?

The Reflect API could be described as a collection or “central place” which houses all kind of object and function related functions (for creation,
property management etc.). Some of the functionalities added on the Reflect object where available before on the Object object.
But the goal for the future is, to have on central place to store all those methods – the Reflect Object/ API.
Therefore, the Reflect API provides useful methods to create, manipulate and query objects and functions in your JavaScript project.

## Object Creation

	Example 1:
	
		class Person {
		  constructor(name){
			this.name = name;
		  }
		}

		let personObj = Reflect.construct(Person, ['Max']); // There is a third argument which is optional
		console.log(personObj);
		console.log(personObj instanceof Person); // returns true
	
	Example 2: Overriding prototype
	
		class Person {
		  constructor(name){
			this.name = name;
		  }
		}

		function TopObj(){
		  this.age = 27;
		}

		let personObj = Reflect.construct(Person, ['Max'], TopObj);

		console.log(personObj);
		console.log(personObj.__proto__ == TopObj.prototype);
	
## Calling functions with Reflect

		class Person {
		  constructor(name, age){
			this.name = name;
			this.age = age;    
		  }
		  
		  greet(){
			console.log(`Hello I am ${this.name}`);
		  }
		}

		let personObj = Reflect.construct(Person, ['Max', 35]);
		// personObj.greet();   This is usual way of calling the function

		Reflect.apply(personObj.greet, personObj, []); // (function, thisObject)
		Reflect.apply(personObj.greet, {name : 'Anna'}, []); 

## Reflect and prototypes

	### Way to get prototype of an object
		class Person {
		  constructor(name, age){
			this.name = name;
			this.age = age;    
		  }
		  
		  greet(){
			console.log(`Hello I am ${this.name}`);
		  }
		}

		let person = new Person();
		console.log (Reflect.getPrototypeOf(person) == Person.prototype); // true
		console.log (person.__proto__ == Person.prototype); // Old style
		
	### Way to set prototype of an object
	
		class Person {
		  constructor(name, age){
			this.name = name;
			this.age = age;    
		  }
		}
		let person = new Person();
		let proto = {
		  age : 30
		};

		Reflect.setPrototypeOf(person, proto);
		console.log (Reflect.getPrototypeOf(person) == Person.prototype); // false
		console.log (Reflect.getPrototypeOf(person)); 

	## Accessing and setting properties with reflect
	
		Example 1:
		
		class Person {
		  constructor(name, age){
			this.name = name;
			this.age = age;    
		  }
		  
		}

		let person = new Person('Max', 28);

		Reflect.set(person, 'name', 'Anna'); // Setting a value using reflect
		console.log(Reflect.get(person, 'name', [])); // Getting a value using reflect
		console.log(person.name); // Usual style
	
		Example 2:
		
		class Person {
		  constructor(name, age){
			this._name = name;
			this.age = age;    
		  }  
		  get name(){
			return this._name;
		  }  
		}

		let mum = {
		  _name : 'abc'
		};

		let person = new Person('Max', 28);
		console.log(Reflect.get(person, 'name', mum)); // Passing the this reference in 3rd argument

	## Creating and deleting properties with Reflect
	
		Example 1: Defining a new property
		
		class Person {
		  constructor(name, age){
			this._name = name;
			this.age = age;    
		  }  
		   
		}

		let person = new Person('Max', 28);
		Reflect.defineProperty(person, 'hobbies', {
		  writeable : true, // property can be changed later as well
		  value : ['Swimming', 'jogging']
		});

		console.log(person.hobbies);
		
		Example 2 : Deleting a property
		
		class Person {
		  constructor(name, age){
			this._name = name;
			this.age = age;    
		  }  
		   
		}

		let person = new Person('Max', 28);
		Reflect.deleteProperty(person, 'age');
		console.log(person.age);
		
		Example 3 : Preventing an object from extension
		
		class Person {
		  constructor(name, age){
			this._name = name;
			this.age = age;    
		  }  
		   
		}

		let person = new Person('Max', 28);
		console.log(Reflect.isExtensible(person));
		Reflect.preventExtensions(person);
		console.log(Reflect.isExtensible(person));