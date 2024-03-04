# React
---
To note:
**Basics**
- React usually runs index.js, which then runs app.js
- Use curly braces to inject javascript code within the html code in the index.js file
- `root.render(const)` will display whatever you want to render in the browser

**React functions**
- defined normally, i.e. `function functionName(props) {`...
- but when we use it, we want to call it like this `const myThirdElement =  <functionName/>`
- props are the attributes that you can give when calling the function
	- props can be called back within the function

**React class**
- class can extend React.Component
- Within the class, there must be a render statement. Within render statemen, there must be a return statement

**Making content dynamic**
- Example: helps to refresh when a new event occurs
- Repeatedly refreshing
	- Can use setInterval(function,1000) to force function to be called every 1000ms for example

- Use the **state** to do this
	- Set the state given the props in the constructor within the class
	- Special methods for `React.Component`s:
		- componentDidMount()
		- componentWillUnmount()
	- Use `setState()` to update the state

- `this is undefined` error:
	- if meet this, need to bind to the constructor
	- `this.update_time = this.update_time.bind(this);`

#webp 