# Proxies

Proxies are an awesome new feature of JavaScript. At first it looks like it's some new cool network wizardry that allows your users to watch the BBC in a different country than the UK. That's not it though! Proxies basically mimic objects and arrays and allow you to do special things whenever you access and/or alter them. Let's see with an example!

```js
var handler = {
    set: function(target, property, value, receiver) {
      console.log('Setting value: ', value);
      target[property] = value;
      return true;
    },
    get: function(target, name){
        return name in target ? target[name] : console.log('We got nothing!');
    }
}

var p = new Proxy([], handler);
console.log(p[0]); // We got nothing;
p.push(42); // Setting value: 42
p[0]; // 42
```

Ok that's pretty cool, but can we do something useful with Proxies? Well, here's an idea: what if we wanted to have an array that's always sorted, whenever you `push`, `pop`, `splice`, `slice`, or whatever? Let's also say we don't want to make some object that implements all of the array methods and everything? Well, that's where Proxies can help!

```js
function Alwaysort(array) {
  var handler = {
      set: function(target, property, value, receiver) {
        target[property] = value;
        target.sort(function (a, b) {
          return a > b;
        });

        return true;
      }
  }

  return new Proxy(array, handler);
}

var sorted = new Alwaysort([]);
```

Alwaysort returns what looks exactly like an array to the caller. You would never know the difference! Now let's try an operation on it.

```js
sorted.push(30);
sorted.push(2);
sorted.push(40);
sorted.push(5);

console.log(sorted); // [2, 5, 30, 40];
```

Pretty awesome right? There's a ton more you can do with Proxies, what are your ideas?
