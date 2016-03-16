# JavaScript Let vs. Var

Constant reader, we have learned a lot about JavaScript variable scope so far. We've read all about hoisting and thisness. That teaches us some of the underlying mechanics of variables, but now let's look at the distinction between the scope of `var` vs. `let`.

Before we look at an example, let's explain variables again! In JavaScript, we normally declare our variables as `var`. For example `var superHungryForMexicanFood = true;` Now, this is perfectly fine, but what exactly does it mean to use the keyword `var`? Well, it means that the variable has function scope and not block scope. Ok, what's all of that fancy talk about? So in other languages, variables typically have block-level scope instead function level scope. In JavaScript this isn't the case. For reference, a block is simply a piece of code wrapped in `{ }` brackets. Computer scientists dissent, but for now that definition will suffice! Now, let's look at an example of `var` in use.

```js
function varScope() {
  for (var i = 0; i < 5; i++) {
    console.log('i is: ', i);
  }

  console.log('outside of block i is: ', i);
}

varScope();
```

The result is:

```bash
i is:  0
i is:  1
i is:  2
i is:  3
i is:  4
outside of block i is:  5
```

You'll see that the variable `i` is still available for the later `console.log` call after the `for` loop block has ended.

What happens though if we change this `var i` to a `let i` instead?

```js
function letScope() {
  for (let i = 0; i < 5; i++) {
    console.log('i is: ', i);
  }

  console.log('outside of block i is: ', i);
}

letScope();
```

The result is:
```bash
i is:  0
i is:  1
i is:  2
i is:  3
i is:  4
Uncaught ReferenceError: i is not defined(…)
```

Now, we get an error! The variable `i` is no longer available in the rest of the function, because it was set as `let` which constrains it to the block. The `var` keyword allowed us to reference `i` anywhere else, but not `let`! This is useful if we want to isolate variables and not "poison" the rest of the function. Maybe we want to reuse `i` and not worry about it being used previously in another block of our function! That's why `let` is handy.
