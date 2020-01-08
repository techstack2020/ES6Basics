# Maps, Sets 

## Map
A Map is a key-value collection introduced in ES6. It kind of fills the gap between arrays (no key-value pairs) and objects (key-value pairs but much
more complex than a simple collection).

### You can create a Map like this:

	let cardAce = {
	 name: 'Ace of Spades'
	};
	let cardKing = {
	 name: 'King of Clubs'
	};
	let deck = new Map();
	deck.set('as', cardAce);
	deck.set('kc', cardKing);
	
	
### You can get values from a map by using :

	deck.get('as');
	
### Get the size of map by :

	deck.size
	
### Iterate through map by :

	let cardAce = {
	  name: 'Ace of Spades'
	};
	let cardKing = {
	  name: 'King of Clubs'
	};

	let deck = new Map();
	deck.set('as', cardAce);
	deck.set('kc', cardKing);


	for(let element of deck.keys()){ // Loop through keys
	  console.log(element);
	}

	for(let element of deck.values()){ // Loop through values
	  console.log(element);
	}

	for(let element of deck.entries()){ //  Loop through key,values
	  console.log(element);
	}

	for(let element of deck){ // Loop through key, values
	  console.log(element);
	}


### Clear a map or delete single items.

	deck.delete('kc'); // Delete a single element
	deck.clear();	// Delete all elements

More information can be found here: https://developer.mozilla.org/enUS/docs/Web/JavaScript/Reference/Global_Objects/Map

## WeakMap

A WeakMap basically also is a Map but it misses some features. 

	* It is not enumerable (you can’t loop through it)
	* It has no size property.
	* It has no clear() method.
	* Cant have primitive types as keys
	
WeakMaps hold weak references to the stored values. That means, if some values aren’t used anymore, they can get garbage-collected and
will be released from the map. That’s also the reason why a WeakMap has no size property.
More information can be found here: https://developer.mozilla.org/enUS/docs/Web/JavaScript/Reference/Global_Objects/WeakMap


## Set

A Set is a collection which only holds values. 
Sounds like an Array? Almost, but a Set will only hold unique values. That means, no value can appear more often than once in a Set.
You can loop through a set to retrieve the values (or use an Iterator). 
You can also clear() a set or delete individual values by using delete().

Remember, each value is unique, therefore you don’t need a key or index to delete a value!
### You can create a Set like this:

	let cardAce = {
	 name: 'Ace of Spades'
	};
	let cardKing = {
	 name: 'King of Clubs'
	};
	let deck = new Set();
	deck.add(cardAce);
	deck.add(cardKing);
	deck.add(cardKing); // Won’t be added, only added once!
	
More information can be found here: https://developer.mozilla.org/enUS/docs/Web/JavaScript/Reference/Global_Objects/Set

## WeakSet

Like a WeakMap, a WeakSet is comparable to a “normal” Set but it only holds weak references.

You may find more information here: https://developer.mozilla.org/enUS/docs/Web/JavaScript/Reference/Global_Objects/WeakSet
