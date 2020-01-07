# Arrays

Some of the new functionalities around arrays are:

## for/of : Loop through the values of an array

### ES5 style:

	let progLangauage = ["Java", "Python", "Javascript"];

	for(let i = 0; i < progLangauage.length; i++){
	  console.log(`I like : ${progLangauage[i]}`);
	}
	
### ES6 style:

	let progLanguages = ["Java", "Python", "Javascript"];

	for(let language of progLanguages){
	  console.log(`I like : ${language}`);
	}
	
## Array.from : Converts a list of values to Array


	function sum(){
	  console.log(arguments);
	  arguments = Array.from(arguments);
	  console.log(arguments);
	  return arguments.reduce((prev, curr) => prev + curr);
	}
	console.log(sum(10,20,30));
	
## find, filter, findIndex methods

	let students = [
	  {
		name: 'Saurav',
		course: 'Maths'
	  },
	  {
		name: 'Dinesh',
		course: 'Physics'
	  },
	  {
		name: 'Venkat',
		course: 'Physics'
	  },
	  {
		name: 'Vinoth',
		course: 'Geography'
	  },
	]

	let physicsStudents = students.find((students) => {
		return students.course === 'Physics';
	});

	let physicsStudentsAll = students.filter((students) => {
		return students.course === 'Physics';
	});

	let index = students.findIndex((students) => {
		return students.course === 'Physics';
	});

	console.log(physicsStudents);
	console.log(physicsStudentsAll);
	console.log(index); 

