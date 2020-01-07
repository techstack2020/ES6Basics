# Classes

Classes are now also available via the class keyword. You may of course
continue using other ways to create objects, but here’s the class-way:

## Example 1:

	class Person {
	  constructor(name){
		this.name = name;
	  }
	  
	  writeName(){
		console.log('My name is :' + this.name);
	  }
	}
	let person = new Person('Max');
	person.writeName();

You may also use inheritance with ES6 classes:

## Example 2: Inheritance example


	class Person {  
	  constructor(name){
		this.name = name;
	  }
	  writeName(){
		console.log('My name is :' + this.name + ', my age is :' + this.age);
		console.log(`My name is ${this.name} and my age is ${this.age}`);
	  }
	}

	class Max extends Person{
	  constructor(age){
		super('Max');
		this.age = age;
	  }
	}
	let maxVar = new Max(27);
	maxVar.writeName();
	
## Example 3 : Static methods

	class Helper{
	  static printMyNameTwice(name){
		console.log(name);
		console.log(name);
	  }
	}

	// let helper = new Helper();
	// helper.printMyNameTwice('Ryan');
	Helper.printMyNameTwice('Ryan');
	
## Example 4 : Import/Export Classes

	myHelper.js
	--------------------
	 class Helper{
		static printMyNameTwice(name){
		  console.log(name);
		  console.log(name);
		}
	  }
	 class RandomClass {  
		getRandomNumber(){
		  return Math.random();
		}
	  }
	 export {Helper, RandomClass}
	 
	app.js
	----------------------
	import {Helper, RandomClass} from './myHelper.js'

	Helper.printMyNameTwice('Kumar');
	let random = new RandomClass();
	console.log(random.getRandomNumber());
	
## Example 5 : Specify getters/setters

	class Person{
	  constructor(value){
		this.name = value;
	  }
	  
	  get name(){
		console.log("Getter Called");
		return this._name;
	  }
	  
	  set name(value){
		console.log("Setter Called");
		this._name = value;
	  }
	}

	let person = new Person('Max');
	console.log(person.name);
	person.name = 'Kumar';
	console.log(person.name);
