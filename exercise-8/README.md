# Events
When we divide apps into multiple components, we often need some way of sending information from child components to their parents.

In [exercise 5](exercise-5/), v-on:click was used to add items to our todo list. Click is just a name for an event, and we can create alternative events for other uses.

An event is simple to create, we just need to `emit`, or send, an event from a component and the parent can choose to listen (or recieve) that event using `v-on`.

Events are emitted like this:
```javascript
this.$emit('click');
```

'click' is the event name, and we can call our event anything we want:

```javascript
this.$emit('somethinghappened');
```

Example of event emitting inside a method:
```html
<template>
  <button v-on:click="emitCustomEvent">Emit event</button>
</template>

<script>
export default {
  name: "ChildComponent",
  methods: {
    emitCustomEvent: function() {
      this.$emit('customevent');
    }
  }
}
</script>
```

The parent can listen to that event like this:
```html
<template>
  <EventComponent v-on:customevent="doSomething"/>
</template>

<script>
import ChildComponent from "./ChildComponent";

export default {
  name: "ParentComponent",
  compoonents: {
    ChildComponent
  },
  methods: {
    doSomething: function() {
      alert("Something happened!");
    }
  }
};
</script>
```

#### Edit Example 8.1 - emit:
[![Edit Example  8.1 - emit](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-emit-g2gtt?fontsize=14&module=%2Fsrc%2FParentComponent.vue)

# Exercise 8
## Create delete button for ToDoItem
For each item in our todo list, we're going to add a delete button. That delete button should remove the todo item from the list.

### Add delete button
:pencil2: First, create a new button under our existing "Done" button. 

:pencil2: The delete button should listen to a click event, and call a delete method. [Exercise 5](exercise-5/) shows how we can add click event listeners.

### Create delete method in ToDoItem
:pencil2: Create a method under the existing "done" method, and use it for the click event on the delete button.

:pencil2: Emit an event from the delete method, called "delete". 

## Update ToDoList component 
:pencil2: We can now modify our ToDoList component so that it can listen to and handle delete events from the ToDoItem component.

### Listen to delete event
Now that ToDoItem can send events, we can listen to them in ToDoList.

:pencil2: Add a `v-on` attribute that listens to the "delete" event in ToDoList.

When the delete event happens, that `v-on` attribute should call a delete method in ToDoList which removes the item.

Our delete method must know which item to delete. We can utilize the index from [exercise 4](exercise-4/) to inform the delete method on which item that sent the click event.

Normal click events are handled like this:
```html
<button v-on:click="methodName">Click me</button>
```

If we want to send additional information through to the click method, we can add variables like this:
```html
<button v-on:click="methodName(index)">Click me with index</button>
```

The method called `methodName` can then recieve the index like this:
```javascript
methods: {
  methodName: function(index) {
    console.log(index);
  }
}
```

#### Edit Example 8.2 - Click with index:
[![Edit Example 8.2 - Click with index](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-click-with-index-v47cr?fontsize=14&module=%2Fsrc%2FClickWithIndex.vue)

:pencil2: Modify the `v-on` attribute on ToDoItem in ToDoList, and send the `index` into the delete method.

The delete method can be empty for now, our you can print out the index as seen in the example.

### Make list editable
In Vue, props are immutable (not editable), and data fields are mutable (editable). This means that we should use data fields for things that can be edited. 

Our todo list is currently a prop, and can't be edited.  We should recreate it as a data field, in order to be able to delete items from it.

Props can be copied into data fields like this:
```javascript
export default {
  name: "PropsToData",
  props: {
    listAsProp: {
      type: Array,
      required: true
    }
  },
  data: function() {
    return {
      listAsData: this.listAsProp
    }
  }
}
```

Here, we recieve a prop called `listAsProp`, and initialize a data field called `listAsData` with a reference to our `listAsProp`.

:pencil2: Use the existing `list` prop and create a new data field that copies that prop. You can call the data field `editableList`.

:pencil2: Replace `list` in the `v-for` attribute with `editableList`, so that the view is updated when we update our list.

### Modify delete method
We can delete items with a given index from a list in JavaScript by using `splice` like this:
```javascript
this.list.splice(index, 1);
```

:pencil2: Modify the delete method so that it deletes the clicked item from the editable list. 

[Exercise 7](/exercise-7/)
[Exercise 9](/exercise-9/)