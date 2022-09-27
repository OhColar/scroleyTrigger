# scroleyTrigger
A lightweight scroll trigger for animating elements using Vanilla Javascript.

**DEMO:** https://ohcolar.github.io/scroleyTrigger/

## What is scroleyTrigger?
scroleyTrigger uses very minimal Javascript to detect whether an element is within the users viewport. If the element is then it applies an active class to it. Using CSS I've written a few basic animations that trigger when the active class is added to an element (more to come) as well as a delay feature.

Both of these combine to create an engaging scrolling experience for the user without the need for a large Javascript library.

## How to use
To initiate the scroleyTrigger on an element simply add a class called `sr` by default the element will fade in when it appears in the users viewport.

## Animation classes
There a a number of animation classes that are pre-built into the package, you can apply them to an element by adding the class name, for example: `fade-down` will fade down the element into view. Default animations are as follows:

```css
fade-up
fade-down
fade-left
fade-right
```

## Variables
One of the things I wanted from this package was animation consistency and at the top of the scss file you'll see a few variables (more to come). These will control the easing speed and the emphasis (for fade-up/down/left/right). 

```scss
$transform-distance: 64px;
$transform-ease: 0.8s;
```

## Delay
Another feature of this package is the animation delay. Using the delay class followed by a number you can specify whether the animation is delayed. A good example of this is if you have elements in a row and would like these to fade in one by one. To add the animation delay use these classes:

```css
delay-1
delay-2
delay-3
delay-4
...
```

I've created a delay loop in the scss file which loops from 1 through 10. If you need to add more delay classes simply change the number 10 to a higher number.
```scss
// Delay Loop
@for $i from 1 through 10 {
    $delay-ms: $i * 0.5;
    &.delay-#{$i} {
      transition-delay: #{$delay-ms}s;
    }
} 
```

## Viewport safe area
There's a safe area defined in the Javascript file, this is known as `rootMargin` - what this does is only trigger the active class when the element is clear of the rootMargin. By default the rootMargin is set to -100px. It's important to have a rootMargin as you may find that the animations and trigger points occur before the user has time to comfortable view the element - feel free to change this value to suit your project.

```js
scrollTrigger('.sr', {
    rootMargin: '-100px'
})
```
