# Vertical Centering in CSS

We landed a man on the moon, we've sent a satellite outside of our solar system, but we still can't center stupid buttons in CSS. Well, actually we can!

One of the trickiest parts of CSS is doing just that. It's not obvious how you get something dead in the middle of your `<div>`. Well, here's how you go about accomplishing that.

```html

<style type="text/css">
  .container {
    position: relative;
    top: 50%;
    left: 50%;
    transform: translateY(-50%);
  }
</style>


<div class="container">
  In the middle
</div>
```

If you would like to do it with more modern and even more straightforward syntax, use flexbox!


```html

<style type="text/css">
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }
</style>


<div class="container">
  In the middle
</div>
```
