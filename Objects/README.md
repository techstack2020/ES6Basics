# Objects

## Short hand methods

Example :

	let flower = {
	  height : 100,
	  color : 'yellow',
	  grow : function(){
		this.height +=5;
	  }
	}

	flower.grow();
	console.log(flower.height);

The above can be changed to :

	let flower = {
	  height : 100,
	  color : 'yellow',
	  grow() {
		this.height +=5;
	  }
	}

	flower.grow();
	console.log(flower.height);
	
## Short hand properties

Example :

	let height = 20;
	let strength = 40;

	let person = {  
	  height : height,
	  strength : strength
	};
	console.log(person);

The above can be changed to :


	let height = 20;
	let strength = 40;

	let person = {
	  
	  height,
	  strength 
	};
	console.log(person);

## Object assignment

Example :

	let person = {
	  nam: 'Ryan',
	  height: '150',
	  strength : 200,
	}

	let warrior = {
	  height: '200',
	  strength : 300,
	}

	let newWarrior = Object.assign({}, person, warrior, {weapon : 'sword', age: '35'});
	console.log(newWarrior);