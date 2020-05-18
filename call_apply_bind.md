
## They are all functions on the Function

### What's the difference between .call and .apply?
- Same just that the way to pass in parameters
- Call with a sequence of arguments
- Apply with list

```js
var x = [1,2,3];
Object.prototype.slice.call(x, 1, 1);
Object.prototype.slice.apply(x, [1, 1]);
```

### Bind is used to fix the `this` keyword to the object

```js
let y = {
  callMe: function() {
    console.log(this); 
  }
}

let x = y.callMe; // reassign function

x.bind(y) // make sure `this` refers to y later
```