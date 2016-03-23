# Object.assign()

What if you have an object and you want to copy it into a new object? Also, what if you want to override some of those properties? How would you do it? The answer is `Object.assign` Let's look at an example to see how it works.

```js
var Car = {
  wheels: 4,
  doors: 4,
  engine: true,
  gasoline: true
};

var HondaCoupe = Object.assign({}, Car, {
  type: 'Civic',
  color: 'red',
  doors: 2
});

console.log(HondaCoupe);
/**
  * Results:
  *  color: "red",
  *  doors: 2,
  *  engine: true,
  *  gasoline: true,
  *  type: "Civic",
  *  wheels: 4
 **/
```

Let's break it down. We use the `Object` global prototype which has the method `assign`. The first parameter it takes is what object you are targeting, and then every parameter afterwards is a source. You could have a hundred of them! We are only taking two in this case. The `Car` object. Then our own custom object. If the custom object has properties with the same keys as `Car`, it just overrides them in the new object. That's all there is to it!
