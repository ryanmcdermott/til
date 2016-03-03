# JavaScript Class Inheritance

Until ES6, JavaScript didn't have a class keyword. Now, joyously, it does! However, this is not a `class` like you would think of in C++ or Java. Really, this is using the same type of prototypal extension and inheritance you see in ES5, it's just much, much prettier.

Let's break all of that jargon down into simpler terms. What is a class in JavaScript? Well, it really is just taking the prototype (the object's template if you recall), and decorating it with what people like to call syntactic sugar. Syntactic sugar is like when you take hard mathematical notation and then instead express it in simple English. It's easier to read and understand. That's what a class allows us to do. If you recall, dealing with the prototype in ES5 [can be hard work](http://ryansworks.com/javascript-prototypal-inheritance/). The class keyword makes that process way easier!

To sum up, the class keyword is just an alternative way of modifying and extending an object prototype.

Let's look at a class and how it allows inheritance. Inheritance gives us the ability to take an object and extend it and overwrite things from the parent. Let's use the classic `Animal` and `Dog` example, with `Animal` being the parent of `Dog`.

```js
class Animal {
  constructor(age) {
    this.age = age;
  }

  speak() {
    console.log('I am an animal');
  }

  dna() {
    console.log('I have animal DNA');
  }
}

class Dog extends Animal {
  constructor(age, breed) {
    super(age);
    this.breed = breed;
  }
  speak() {
    console.log('ruff!');
  }
}

var puppy = new Dog(1, 'terrier');
console.log(puppy); // Animal {age: 1, breed: 'terrier'}
puppy.speak(); // ruff
puppy.dna(); // I have animal DNA
```

As you can see, even though `Dog` itself doesn't have an `age` variable, its parent does. We call `super()` and pass that variable in, which calls the constructor of `Animal`, and now our `Dog` object has an age. Moreover, our `Dog` object doesn't have a `dna` method, but since our parent `Animal` does, we can call that on our `puppy` instance of `Dog`. Finally, `Dog` can overwrite parent functions, in this case we overwrite `speak` because ruff is the sound that dogs make!
