# Swift By Example: Values

Swift has a lot of the same kinds of value operators and expressions that you might be familiar with in other languages. Without getting into a bunch of theory, let's just look at some code and figure out how values work in Swift.

```swift
print("hello " + "world")
print("1+1 =", 1+1)
print("7.0/3.0 =", 7.0/3.0)
print(true && false)
print(true || false)
print(!true)
```

You'll notice, the `+` sign is overloaded as a concatenation operator, just like you would see in dynamic languages such as Python or JavaScript. That means, it can do addition like `1 + 1`, but it can also combine two strings together such as `hello` and `world`.

Floating point arithmetic (that is to say, the `7.0 / 3.0` expression), operates like normal. The boolean expressions (`true && false` for example) are the same as what you would see in other languages.

Let's see what values it produces! Save this as `values.swift`.

To compile this and run in real-time, we can open up our handy Terminal, and type the following command:

```bash
$ swift values.swift
hello world
1+1 = 2
7.0/3.0 = 2.3333333333333335
false
true
false
```
