### `this` keyword in javascript


- Refer to the context that it is called. So this is determined at run time

```js
function Car(model) {
  this.model = model;
}

Car.prototype.drive = function() {
  console.log("driving ", this.model, "!");
}


var x = new Car("BWM");
x.model  // here this is the object, which is the one created from Car object.
x.drive() // this also refers to this object when the method is called.

```

- How about call, apply, bind

```js
function fn() {
  console.log(this);
}

var obj = {
  value: 5
};
var boundFn = fn.bind(obj);

// Here we lock the object into the `this`. So `this` is the obj
```

- Changing the object

```js
var obj = {
    value: 5,
    printThis: function() {
      console.log(this);
    }
};
obj.printThis(); // -> { value: 5, printThis: ƒ }

var newObject = {
  value: 4
}
obj.printThis.call(newObject); // {value: 4}
```

```js
var obj = {
    value: 'hi',
    printThis: function() {
        console.log(this);
    }
};
var print = obj.printThis;
obj.printThis(); // -> {value: "hi", printThis: ƒ}
print(); // -> Window {stop: ƒ, open: ƒ, alert: ƒ, ...}
```


```js
var obj1 = {
    value: 'hi',
    print: function() {
        console.log(this);
    },
};
var obj2 = { value: 17 };

obj1.print.call(obj2); // -> { value: 17 }
new obj1.print(); // -> {}
```