# Node.js
---
## Good to know
Some useful variables:
`__dirname, __filename`

## Module
Modules are a key part of Node.js
Allows you to import another JS file as a module
- use the require() function
console.log(module) gives all the properties of current module
can export modules in javascripts too 

**Built-in modules**
| Name                   | Purpose                                   |
| ---------------------- | ----------------------------------------- |
| os                     | provide os utility methods and properties |
| path                   | work with file and dir path               |
| fs                     | interact with file sys based on POSIX fn  |
| [[#HTTP module\|http]] | use features of the HTTP protocol         |

importing step example: `const fs = require('fs')`

## Characteristics
asynchronous and non-blocking by default. blocking versions available for most functions but not recommended because it will slow things down alot


## Event Driven Programming

**Callbacks**
- Callbacks are a function that is called when a task is completed
- It can be synchronous, but it is usually asynchronous
- Example of synchronous callback
```javascript
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
```

**Promises** Object
The Promise object **represents the eventual completion (or failure) of an asynchronous operation and its resulting value**. Use promise chaining when you want to schedule asynchronous functions before another function.
- Remember, a Promise is like an **Interface** data type

How to construct: A new Promise takes in ONE parameter
- The ONE parameter is a **function**, which has TWO methods, resolve and reject
- The **resolve** method will call the **.then() method** of the promise, which is specified by user
	- the .then() method takes in a function, where the variables are the arguments (e.g. message) passed to the resolve method, and you could print that message, or do more stuff upon that promise has finished
- The **reject** method will call the **.catch() method** of the promise, which is specified by user
	- the catch() method will spring into action any time there is an error along the promise chain

**Async/Await** syntactic sugar
- When Async is written in front of a function, the function will return a promise
	- The return value of the function is automatically set as the resolve method's parameter
- Await allows a promise to be resolved to the value of a variable; until then, **PAUSE**
	- pause the execution of this function, until the promise resolves to a value
	- In this example `const a = await getFruit()`, the await keyword not only waits until getFruit() resolves, the "then" function will be like "set a = the resolve method parameter"

- A promise is a function that stores the asynchronous functions
	- If got multiple async fns, then need to `promise.all` in order to wait for all the multiple async functions to complete
	- the function inside the promise needs to return something (cannot be return nothing)
	- remember to return the async function
- Once the function inside the promise is done, 
	- the function will notify the promise that it is done.
		- this is done using the .then(notify function)
	- If an error occured, the function will notify the promise of such an error
		- this is done using the .catch(error function)
- Need to set **await** keyword outside promise, in order to wait for the promise to finish. 
- Some example code

```node
const queriesList = [];

    loyaltyPrograms.map(program => {
      queriesList.push(
        client.uploadFile(`./transfers.csv`, `./transfers.csv`)
      );
    });

    await Promise.all(queriesList)
    .then(() => {
      console.log("all done");
    })
    .catch(err => {
      console.log("fuck yo");
    })
```

However, sometimes other people cannot deal with multithreaded requests (like sftp servers). Similar to [[HTTP##Non persistent HTTP|interleaving portion here]]
Therefore, if there are errors (like this one: write empty file because it closes its current thread when it receives a new task) then need to consider doing things synchronously.
```node
await Promise.all(loyaltyPrograms.map(async (program) => {

      //* Upload local file to remote file
      try {
        const response = await client.uploadFile(`./${program}.csv`, `./${program}/${program}.csv`);
        console.log(`${program} File Uploaded.`);
        return response;
        
      } catch (error) {
        console.log(`Error ${error.message}`);
      }
      // console.log(`sending ${program} file now`);
    }));
```

## HTTP module
got createServer() method that services a incoming request (req) and smth to send back (res)
- can do an if else conditional on the req to serve different pages (res.end('insert some text depending on the req.url'))
- Note that res.end() function will end the server function upon it has finished running
- server has on method that can listen for a request event
- Use the writeHead() function to specify the type of data that you are sending back (so you are providing metadata, like oh this is a html file that you are receiving, browser!)
- readFileSync() is used to actually send back a html file instead 
#webp