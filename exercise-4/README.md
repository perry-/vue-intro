# List rendering (v-for)
v-for is a Vue directive (similar to HTML attributes) which enables us to create repeating content in our HTML templates. This can be achieved by iterating over lists (known as arrays) in our data model (either from computed values, data or props).

Let's say we have a list named "toDoItems" in our data model, then we can iterate through that list by using the syntax `toDoItem in toDoItems`. `toDoItem` is an example of an alias, and represents the current element in our for loop. We can name that alias whatever we want (like `something in toDoItems`), but the common pattern is to use the same aliases for both our list and list item, where the list pluralized (like `item` for list item, and pluralized form `items` for the actual list).

`toDoItem in toDoItems` is used as a value for the v-for directive/attribute:

```html
<ul>
  <li v-for="toDoItem in toDoItems">
    {{ toDoItem }}
  </li>
</ul>
```

Here's an example of v-for in a complete component:
```html
<template>
  <ul>
    <li v-for="toDoItem in toDoItems">
      {{ toDoItem }}
    </li>
  </ul>
</template>

<script>
export default {
  name: "OurCustomComponent",
  data: function() {
    return {
      toDoItems: ['Buy milk', 'Feed the cat']
    }
  }
};
</script>
```

This component will render the following HTML:
```html
  <ul>
    <li>Buy milk</li>
    <li>Feed the cat</li>
  </ul>
```

## List keys
Say we have the following list of items: `['Buy milk', 'Buy milk']`. If one of those items were to change, Vue will struggle to see the difference between them. That's why we're required to give each item a unique key:

```html
  <ul>
    <li v-for="(toDoItem, index) in toDoItems" :key="index">
      {{ toDoItem }}
    </li>
  </ul>
```

In the example above, we use the `index` as the key. We can get the index by expanding our previous v-for value (`toDoItem in toDoItems`) with `index`: `(toDoItem, index) in toDoItems`. The key binding/attribute can then use that key, since each index is unique within the for loop. `:key="index"` sets the key for each list item (`<li>`). In some cases, the `index` will not be unique, but we can assume so for this example.

#### Edit Example 4.1 - v-for:
[![Edit Example 4.1 - v-for](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-v-for-3hqlg?fontsize=14&module=%2Fsrc%2FApp.vue)

# Exercise 4
## Import ToDoItem into ToDoList
First, we need to import ToDoItem into ToDoList, so that we can use it in ToDoList directly. This replaces the `<slot>` method from previous exercises. 

:pencil2: Import ToDoItem into ToDoList, see how to use `import` in [exercise 3](exercise-3/)

### Add ToDoItem as subcomponent in ToDoList
In order for Vue to recognize ToDoItem as a subcomponent in ToDoList, we will have to add it to a `components` definition. Vue components can declare imported components as subcomponents by placing them in the `components` field like this:

```javascript
import ComponentName from "./components/ComponentName";

export default {
  name: "OurCustomComponent",
  components: {
    ComponentName
  }
};
```

:pencil2: Add ToDoItem as a subcomponent in ToDoList, so that we can use it in our template.

## Add list prop in ToDoList
In the previous exercise, we added `props` to the ToDoItem component.

:pencil2: Repeat that for ToDoList and add 'list' as a prop. That prop should be an `Array` and it should also be required (an empty list/Array is allowed). See [Exercise 3 - props](exercise-3/) for reference. 

## Add ToDoList in App.vue
Import ToDoList in App.vue in the same way as you imported ToDoItem in ToDoList (as in the example above).

## Define a list of TODO items in App.vue
:pencil2: Add a new field in the `data` entry in App.vue. You can call it whatever you want, but if you're out of ideas, we suggest `toDoList` (naming things is hard!). Use that field as a value for the `list` prop on the ToDoList component. The result should be a list that's sent from App.vue into ToDoList. In order to send a list into `list`, it will need to be written like this (with a colon):

```html
<ToDoList :list="toDoList" />
```


Tip: If you want to verify that the `list` prop is actually sent into ToDoList, you can modify the template in the ToDoList component and print out your list prop like this:

```html
<template>
  <ul>
    {{ list }}
  </ul>
</template>
```

## Repeat ToDoItem in ToDoList
:pencil2: Use v-for to repeat ToDoItems in the ToDoList component. The v-for attribute should use our `list` prop and add a ToDoItem for each item in that list. 

[Exercise 3](/exercise-3/)
[Exercise 5](/exercise-5/)