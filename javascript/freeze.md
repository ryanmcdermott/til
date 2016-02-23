# Constant Objects and Freezing

The `const` keyword in JavaScript doesn't do exactly what you might think it would do. For basic primitive values it does the obvious.

```js
const str = 'test';
str = 'blah';
console.log(str);

"test"
```

However, for objects this isn't the case. Look at this example:

```js
const foo = {baz: 'bar'};
foo.baz = 'test';
console.log(foo);

Object {baz: "test"}
```

Even though `foo` is set as a constant, the key baz can still be modified. To keep an object from being modified at all, use `Object.freeze()` like so:

```js
const foo = {baz: 'bar'};
Object.freeze(foo);
foo.baz = 'test';
console.log(foo);

Object {baz: "bar"}
```