# slots

When creating custom components, we need a way to nest them just the way we do with basic HTML. The Web Components spec was created in order to create custom componentst just like the one we created in Exercise 1. We'll use _slots_ from the Web Components spec to achieve nesting, just like this:


```html
<OurCustomComponent>
  <p>Regular HTML</p>
</OurCustomComponent>
```

OurCustomComponent is a custom Vue component with support of inner HTML. OurCustomComponent has the following structure:

```html
<template>
  <div class="our-custom-component">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "OurCustomComponent"
};
</script>
```

The resulting HTML will look like this:
```html
<div class="our-custom-component">
  <p>Regular HTML</p>
</div>
```

OurCustomComponent is basically a wrapper for `<p>Regular HTML</p>`. We can place the slot wherever we want in the template code, just not as the root element (the element that goes right inside `<template>`).

#### Edit Example 2.1 - slots:
[![Edit Example 2.1 - slots](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-21-slots-vqwb7?fontsize=14&module=%2Fsrc%2FApp.vue)

# Exercise 2
## Create a list component

:pencil2: Create a new component in the same project as from Exercise 1. Call this component `ToDoList`.
The ToDoList component should wrap a `ul` element around whatever we put in the inner HTML.

:pencil2: In App.vue, use ToDoList as a wrapper around several ToDoItem components, so that the resulting HTML will look like this:

```html
<ul>
  <li>Buy milk</li>
  <li>Buy milk</li>
  <li>Buy milk</li>
</ul>
```

Note that we will end up with a TODO list with one repeating TODO item (since we're reusing the same ToDoItem component)

[Exercise 1](/exercise-1/)
[Exercise 3](/exercise-3/)