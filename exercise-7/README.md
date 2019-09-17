# Dynamic classes (v-bind classes)
You can bind class names to tags using `v:bind`:
```html
<div v-bind:class="className"></div>
<!-- Short cut -->
<div :class="className"></div>
```

We can pass an object to v-bind:class to dynamically toggle classes.
You can have multiple classes toggled by having more fields in the object.

```html
<div v-bind:class="{ active: isActive }"></div>
```

# Excercise 7
## Add done button for todo items

:pencil2: In the component `ToDoItem`, add a button where you use `v-if` to hide the `Done` button when isDone is true.

:pencil2: Add an event `@click` and add a function name, for example `setToDone` with the text `Done`.

:pencil2: Add the data field in data, for example `isDone`, and set it to false.

:pencil2: In methods, add a function to set `isDone` to true.

It should look like this:
```js
setToDone: function() {
  this.isDone = true;
}
```

Then in the HTML template add a <span> with the class.
HTML should look like this:

```html
<span :class="{done: isDone}">{{ text }}</span>
```

## Styling / CSS

:pencil2: Now add the style you want to appear on the text when the button is clicked.

```css
<style scoped>
.done {
  text-decoration: line-through;
}
</style>
```

[Exercise 6](/exercise-6/)
[Exercise 8](/exercise-8/)