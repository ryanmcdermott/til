# Swift By Example: Hello World

Swift is a rich language that can be used for all sorts of apps, not just iOS or OSX GUI ones. We can make terminal apps just like we would with any other systems language like C++ or Java!

Let's start off with a Hello World example!

What does Hello World look like? Open up your favorite editor and type this:

```swift
print("hello world")
```

Save this as `hello-world.swift`.

To compile this, we can open up our handy Terminal, and type the following command:

```bash
swiftc hello-world.swift
```

Now we have a binary! To run it, type the following command in the same directory:
```bash
./hello-world
```

## For the Neckbeards (4NB):
Swift has no main function! That's right. Just like JavaScript, the entry point is whatever the first line of code is in the global scope of your file/module. If you are using Cocoa APIs then the main function is `@UIApplicationMain` in your `AppDelegate.swift` file.

You can also run the app without compiling it by just running the following:

```bash
swift hello-world.swift
```
