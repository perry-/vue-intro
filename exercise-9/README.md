# List handling
Sometimes, we need to update complex lists in Vue. Vue knows how to rerender lists when we add or delete items as we did in [Exercise 5](exercise-5/) (add) and [Exercise 8](exercise-8/) (delete). When we update a list item, Vue does not automatically rerender the view. 

So, we need to update items in a list by using a Vue method called `set`. It is a global method like `emit`, and looks a bit familiar:
```javascript
this.$set();
```

In contrast to `emit`, `set` takes three arguments (or values). Those are:
1. The list we want to update
2. What index or list item we want to update
3. The new value for our list item

So, if we add those to the `set` method, it will look like this:
```javascript
this.$set(this.list, 1, "New text");
```
The code above will update the item in index 1 in `this.list` with the value "New text".

We can replace the values above with variables to make it more dynamic:
```javascript
this.$set(this.list, index, this.newText);
```
`index` can be the current index, and `this.newText` can point to any data field (or a computed value or prop).

The `set` method is not restricted to lists. For those that want to dig deeper, visit [the official Vue documentation about reactivity](https://vuejs.org/v2/guide/reactivity.html).

# Exercise 9
In this exercise, we're going to add an edit mode to our todo list.

## Make ToDoItem editable
### Split ToDoItem into edit and view
ToDoItem must handle two modes: edit and view.

:pencil2: First, create a data field in ToDoItem called `editMode` and set the value to`true`. This field will help us determine if the view should display editable fields or just text.

`v-if` can be used to hide and show items based on edit mode. In our situation, we need to show a set of editable fields if `editMode` is `true`, and hide them if not. `v-if` has a corresponding `v-else` for this scenario:

```html
<template>
  <template v-if="mode">
    This will be shown if "mode" is true (and hidden if false).
  </template>
  <template v-else>
    This will be shown if "mode" is false (and hidden if true).
  </template>
</template>
```

#### Edit Example 9.1 - v-else:
[![Edit Example 9.1 - v-else](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-v-else-8qlwx?fontsize=14&module=%2Fsrc%2FElse.vue)

:pencil2: Add two `<template>` elements into the `<li>` element in ToDoItem.

The first `<template>` item should be shown if ToDoItem is in edit mode.
:pencil2: Add an input field to the first `<template>` item.

The second `<template>` item should be hidden if ToDoItem is in edit mode.
:pencil2: Add text to the second `<template>` item (we will change this text later).

Try to change `editMode` to `false` and verify that your text is displayed instead of the `<input>` field.

### Add edit button
We should be able to toggle edit mode without manipulating the code.

:pencil2: Add a button in the first `<template>` and call a method that sets `this.editMode` to `true`, when the button is clicked.

### Add save button
When we're done editing, we need to update the list item with the new text.

:pencil2: Add a save button in the second `<template>`, and create a save methood that gets called on click.
:pencil2: Set `this.editMode` to `false` when the save button is pressed.

### Emit saved text
`$emit` can send information from the child component to the parent like this:

```javascript
this.$emit('eventname', this.information);
```

Emit `this.editableText` from ToDoItem when save button is pressed. Use "input" as the event name.

## Update list in ToDoList
### Add input event listener
:pencil2: Use `v-on` as an attribute on ToDoItem so that ToDoList listens to the "input" event.

`this.$set` requires three arguments:
1. The editable list in ToDoList
2. Index for the edited ToDoList item
3. The new text from the "input" event

:pencil2: Create a method called `updateItem` and give it two arguments: `index` and `text`.

We will have to expand `v-on` to combine values from both child and parent component:
```html
<CustomComponent v-on:input="(text) => methodName(index, text)" /> 
```
Here, the `v-on` contains a method that receives the `text` from `CustomComponent` and sends it into another method in the parent component (denoted by the `=>`/arrow). It also sends `index` from the parent component into the method: `methodName(index, text)`.

:pencil2: Modify `v-on` on ToDoItem in ToDoList, so that it recieves the `text` from ToDoItem and sends both `text` and `index` into the `updateItem` method. 

### Update list with this.$set
:pencil2: Update `this.editableList` using `this.$set` in the `updateItem` method. Remember to add both `index` and `text` as arguments. 

[Exercise 8](/exercise-8/)