# Promises

Promises are a great addition to handle asynchronous tasks/ callbacks. As the name implies, a Promise promises to return a certain value – even if the
underlying task fails. In such a failure case, the promise would be rejected but the caller would still be informed.

Therefore, a promise is created with a resolve and reject function being passed as arguments. Depending on the result, the appropriate function is
executed and a possible return value is passed as an argument.

Example 1: 

	let promise = new Promise(function(resolve, reject){
	  setTimeout(function(){ // setTimeout to simulate async task
		resolve("Resolved");
	  }, 1000);
	  
	});

	promise.then(function(data){
	  console.log(data);
	});

Example 2:

	let promise = new Promise(function(resolve, reject){
	  setTimeout(function(){ // setTimeout to simulate async task
		resolve("Resolved");
	  }, 1000);
	  
	  setTimeout(function(){
		reject("Rejected!");
	  }, 1500);
	  
	});

	promise.then(function(data){
	  console.log(data);
	}).catch(function(error){
	  console.log(error);
	});

Example 3: 
Usage of all method. If all promises resolve then method is called. If any promise rejects catch callback is called.

	let promise1 = new Promise(function(resolve, reject){
	  setTimeout(function(){ // setTimeout to simulate async task
		resolve("Resolved 1");
	  }, 1000);
	});

	let promise2 = new Promise(function(resolve, reject){
	  setTimeout(function(){ // setTimeout to simulate async task
		resolve("Resolved 2");
	  }, 1000);
	});

	Promise.all([promise1, promise2])
		  .then((success) => console.log(success))
		  .catch((error) => console.log(error));
	  
Example 4: 
Usage of race method. If the first promise that completes execution resolves sucess is returned otherwise error.

	let promise1 = new Promise(function(resolve, reject){
	  setTimeout(function(){ // setTimeout to simulate async task
		reject("Rejected 1");
	  }, 1000);
	});

	let promise2 = new Promise(function(resolve, reject){
	  setTimeout(function(){ // setTimeout to simulate async task
		resolve("Resolved 2");
	  }, 800);
	});


	Promise.race([promise1, promise2])
		  .then((success) => console.log(success))
		  .catch((error) => console.log(error));