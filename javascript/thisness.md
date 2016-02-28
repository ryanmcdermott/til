# Can't Touch This

In JavaScript, the most confusing thing is what the heck `this` is or even refers to in a function. Most of the time it seems like `this` is just referring to the current function, but actually in JavaScript, `this` refers to the **calling context**. Let's look at an example to see what that means:

```js

function Animal(species) {
  this.species = species;
}

Animal('dog');
```

What does `this.species` refer to here? It actually refers to the global `window` variable of the browser! The function `Animal` was called in the context of the global `window` object. After running that, try printing `console.log(window.species);` and see what you get to confirm.

If we make one modification though, we can get `this` to refer to something else and not `window`. We just have to call `new` on the function.

 *(run this in a different browser tab):*

```js
function Animal(species) {
  this.species = species;
}

var dog = new Animal('dog');
console.log(dog.species); // dog
console.log(window.species); // undefined
```

Now, `this` is a referring to a new instance of `Animal`, in this case it's the variable `dog`

The `this` variable has even more interesting characteristics when you look at how you can refer to a specific object as the calling context by calling or applying it to that. Let's see an example of that, and note the invocation of `Restaurant.apply`:

```js
function Restaurant() {
  console.log(this.menu);
}

var obj = {
  menu: [
    'Hamburger', 'Pizza', 'Salad'
  ]
};

Restaurant.apply(obj); // ['Hamburger', 'Pizza', 'Salad'];
Restaurant(); // undefined
```

To summarize, `this` can be whatever you want it to be, if you just specify which object it's referring to. If you don't specify one via `apply`, `call`, or `new`, then it will refer to the global `window` object.
