# JavaScript Prototypal Inheritance

In JavaScript, there's no such thing as classes (well sort of not totally true anymore). Anyway, in JavaScript, everything is an object. The question is, how do objects inherit from each other? Well, they do so by extending the prototype chain of another object. Let's take a look at what that means in an example:

```js
// Parent function
function Animal(age) {
  this.age = age;
}

// Parent class method
Animal.prototype = {
  constructor: Animal,
  speak: function () {
    console.log('generic speak function');
  },
  dna: function() {
    console.log('I have animal DNA!');
  }
}

// Child class constructor
function Dog(breed, age) {
  Animal.call(this, age);
  this.breed = breed;
}

// Inherit from the parent class
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.speak = function speak() {
  console.log('ruff!');
}

var puppy  = new Dog('terrier', 1);
console.log(puppy); // Dog { age: 1, breed: 'terrier'}
console.log(puppy.speak()); // ruff!
console.log(puppy.dna()); // I have animal DNA
```

That's a lot of code. Let's start from the beginning to understand.

We create an Animal function that will begin to construct our `Animal` object. We set that as the constructor on the `Animal` prototype. Think of the prototype as the template for any object. In this case, our objects are animals, fluffy and furry! After we do this, we can set instance methods and variables, which we do with the methods `speak` and `dna` because all animals can speak and they have DNA!

Now how would we create a dog? Well, we do the same thing. We create a function for a `Dog`. Except here's the key: We do this: `Animal.call(this, age)` which basically calls the `Animal` function in the context of `Dog`. It passes the relevant variables `age` to the `Animal` parent object. We want the constructor of the parent, `Animal`, to set the age of our little doggy!

Subsequent to that, we do one more thing that's very important: we call `Dog.prototype = Object.create(Animal.prototype)`. What this will do is set our `Dog` object's prototype to inherit from Animal. It copies it's template basically. You'll notice that because of this, the puppy object still has the method `dna`. Our `Dog` object doesn't have that method explicitly, but its parent `Animal` does. That is the power of inheritance. We can also overwrite parent methods, as you can see with the method `speak` on `Dog`, because that's the sound dogs make!

Next time, I'll discuss the ES6 syntactic sugar of `class` which makes this process dramatically simpler.
