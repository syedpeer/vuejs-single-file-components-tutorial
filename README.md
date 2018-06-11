---
title: An introduction to Single File Components in VueJS
published: false
description: What are Single File Components in VueJS and how do you use them? This article will give you an introduction with some examples and why you should be using them
tags: vuejs, javascript, beginners
cover_image: https://images.unsplash.com/photo-1526374870839-e155464bb9b2?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=a34afeffc0b1dc2552ba82d61ea37204&auto=format&fit=crop&w=750
---

## What are they?

Single File Components are a fairly easy concept to understand.  In the past you've had to create three separate files for your component(s):

- One HTML file for the structure;
- One JavaScript file for the behaviour and dynamic content;
- One CSS file for the layout and styling.

The reason for this was to create a separation of concerns.  The designer could work on the styling, separately from the developer who built the structure and behaviour.  

This becomes redundant when you use an intelligent version control system that can assist with merge conflicts when more than one person is changing the same file.

Single File Components encapsulate the structure, styling and behaviour into one file.  Here's an example file:

```vue
<template>
    <div>
        <h1>Welcome!</h1>
        <p>Hello, {{ name }}!</p>
    </div>
</template>

<script>
    module.exports = {
       data: function() {
           return {
               name: 'Sam'
           }
       }
    }
</script>

<style scoped>
    p {
        color: #33c689;
        letter-spacing: 3px;
    }
</style>
```


At first look, it seems strange to have all of this in one file, but it actually makes a lot more sense.

In case you were wondering what "scoped" means, it limits this css to only apply to this component, so you're free to write changes to global tags without it actually affecting those tags outside this component, briliant eh?!

## Why?

How often have you had to trawl through pages of CSS to try and find the part you need to work on.  Even worse, your component could have it's style taken from many different parts of that file.  A class here, an id there, and somewhere in the middle a change to the global functionality of a tag.  Not nice to maintain and where do you add new styles if you're trying to be a good developer?

Secondly, the html could have repeated components all over the place, there's no real re-use of structure.  You're also created mental walls between the styling, structure and behaviour of your component.

Finally the behaviour, by which we generally mean the JavaScript.  Again we're stuck with code that is split across files as the original developers decided at the time.  One project it's all in one file, another it's split by pages, another it's split by domain.  

With single file components, there really is just one place for everything.  Easy to read and understand, easy to maintain and easy to develop.

## What else?

Single file components not only support HTML and CSS, you can also use a templating language like [pug](https://pugjs.org) or a CSS pre-processor like [SASS](https://sass-lang.com/).  Here's an example that uses both:

```vue
<template lang="pug">
div
  h1 Welcome!
  p Hello, {{name}}
</template>

<script>
module.exports = {
  data: function () {
    return {
      name: 'Sam'
    }
  }
}
</script>

<style lang="sass" scoped>

  $primary-colour: #33c689;
  $letting-spacing: 3px;

  p
    color: $primary-colour;
    letter-spacing: $letting-spacing;
</style>

```

You're not limited to pug or sass, there's many other options out there: PostCSS, Stylus, TypeScript and more.  Anything that has a loader for webpack should be supported.

## What about React?

With React, the structure (html) and behaviour (javascript) are brought together into the JSX definition.  You could also inline your styling here, but that's generally considered bad practice.  This leaves the CSS in separate files again, leaving you in a mess.  There are a few libraries out there to allow you to include CSS in your components, but there's no standard, so you're likely to see one library in one project and a different library in another project, which makes it inconsistent and harder to learn.

## Summary

I hope that I've whet your appetite around giving Single File Templates a go, I've created a simple github repo [vuejs-single-file-components-tutorial](https://github.com/sambenskin/vuejs-single-file-components-tutorial) so you can just clone it and run it.  If you've never used VueJS before, I strongly recommend also checking out the [documentation](https://vuejs.org/v2/guide) and there is also a free video course at [vueschool.io](https://vueschool.io/)
