# Click events
Events give components interactivity. A button doesn't do anything until it's used with a click event listener. 

A component that contains a button can "listen" to the click event using the `v-on` directive/attribute:
```html
<button v-on:click="method">Click me</button>
```
The button in this example will invoke the method called "method" when clicked.

`v-on` can be replaced with the `@` symbol like this:
```html
<button @click="method">Click me</button>
```

All exercises in this course will use `v-on`, but there's no difference.

#### Edit Example 5.1 - Click event:
[![Edit Example 5.1 - Click event](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-click-event-m58u3?fontsize=14&module=%2Fsrc%2FClickEvent.vue)

# Methods
Methods enable us to gather code into a single block for reusability. Methods are just a collection of JavaScript functions, and can be invoked from anywhere in the component context.

Methods are usually used in pair with events, but a method can also be called from another method like this:
`this.method();`

Methods can also recieve parameters just like regular JavaScript functions:
`this.method(params);`

The methods field is as mention a collection of method names and their corresponding JavaScript functions:

```javascript
export default {
  name: "ComponentName",
  methods: {
    alertMe: function() {
      alert("Alert!");
    }
  }
}
```

## What's this?
We use `this` when we refer to the current component context inside a method. `this` will contain all data fields and methods defined in the current component. As you may have noticed, we don't need to prepend `this` to things like data fields or methods when they're used in `template`:

```html
<template>
  <div>
    <button v-on:click="alertMe">Click me</button>
    {{ dataField }}
  </div>
</template>

<script>
export default {
  name: "ComponentName",
  data: function() {
    return {
      dataField: "Hello world"
    };
  },
  methods: {
    alertMe: function() {
      alert(this.dataField);
    }
  }
};
</script>
```

The resulting HTML will look like this:
```html
  <div>
    <button>Click me</button>
    Hello world
  </div>
```

#### Edit Example 5.2 - This:
[![Edit Example 5.2 - This](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-52-this-nwps3?fontsize=14&module=%2Fsrc%2FThis.vue)

# v-model
`v-model` allows us to create a two-way data binding on form elements, like `input`.

```html
<input v-model="message" />
```

You can bind a form element value to a data field, and the data changes with the value of the field.

Data field values can be printed using  in the HTML like this:
```javascript
{{ dataField }}
```

These examples can be used in combination to print the message from an input field directly into the rendered HTML:
```html
<input v-model="message" placeholder="Enter a message">
<p>Message is: {{ message }}</p>
```

#### Edit Example 5.3 - v-model:
[![Edit Example 5.3 - v-model](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-52-v-model-8uymi?fontsize=14&module=%2Fsrc%2FVModel.vue)

# Excercise 5
## Create input field
:pencil2: In App.vue, add a data field we can use as the `v-model` value. The data field can be named anything, like `newItem`. The data field should contain an empty string (""):

```javascript
data: function() {
  return {
    dataField: ""
  }
}
```

:pencil2: Add a `input` element to App.vue, and add a `v-model` to it. Use `newItem` (or the name you used) as a value for `v-model`.

## Create add button
:pencil2: Add a new button to App.vue, the button text should be "Add".

## Create method to add items
We can add items to a list in JavaScript by using `push`:
```javascript
this.list.push(this.something);
```

:pencil2: Add a click event for the "Add" button. That click event should call a method which in turn should add `newItem` to `toDoList`.

[Exercise 4](/exercise-4/)
[Exercise 6](/exercise-6/)