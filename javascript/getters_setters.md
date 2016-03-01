# Getters and Setters

A cool but infrequently used feature of JavaScript is getters and setters. These allow you to perform custom behavior when an object is viewed or manipulated. Let's take a look at an example:

```js
var Restaurant = {
  _manager: null,
  get manager() {
    console.log('getting manager');
    return this._manager;
  },
  set manager(m) {
    console.log('setting manager');
    this._manager = m
  }
};

Restaurant.manager = 'John Smith'; // 'setting manager'
Restaurant.manager; // 'getting manager' 'John Smith';
```

## Why would we want to use this?

Well, if we wanted to save data to a log about how and when our objects have been modified, that could be one use case. Another interesting use case could be if this `Restaurant` object were an API and we wanted to change a DOM node to reflect our new manager, all an API consumer would have to do is change the `manager` variable and immediately it would be reflected on the DOM. There are a lot of potential ideas!

*Note: typically, the internal variable that the getter and setter refer to is prefixed with an underscore*
