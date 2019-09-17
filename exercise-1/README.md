# Basic component structure
Vue components contain three main ingredients:

## Template / HTML
```html
<template>
  <p>{{ model }}</p>
</template>
```

## Logic / JS
```js
<script>
export default {
  name: "ComponentName",
  data: function() {
    return {
      model: "Hello"
    }
  }
}
</script>
```

## Styling / CSS
```css
<style scoped>
p {
  font-size: 2em;
  text-align: center;
}
</style>
```

#### Edit Example 1.1 - Hello world:
[![Edit Example 1.1 - Hello world](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/hello-world-pn6lh?fontsize=14&module=%2Fsrc%2FComponentName.vue)

# Exercise 1
## Create ToDoItem component

:pencil2: Create a ToDoItem component for our TODO list. This component should show a static text, f.ex. "Buy milk". 

The following Code Sandbox has what you need for creating a component, but it's missing some template code and a proper component name. Use the same code for this exercise and all following exercises.

#### Click here to start:
[![Click here to start](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/vue-template-nj26j)

Code Sandbox contains a solutions folder with solutions for each exercise if you're stuck.

[Exercise 2](/exercise-2)