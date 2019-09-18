# Props
`Props` are used to send information from a parent component to its children. Props are much like regular HTML attributes. We can give them any name as long as they don't collide with standard HTML attributes.

Props are one-way: from parent to child. Any time the parent changes the value of the prop, the new value is sent to the child and the component is re-rendered.

## Child component

```html
<template>
  <h3>{{ postTitle }}</h3>
</template>
<script>
export default {
  name: 'BlogPost',
  props: ['postTitle']
}
</script>
```

Components can be imported into other components, and be reused multiple times. This import method is standard to the latest version of JavaScript, and the syntax looks like this:

```javascript
import ComponentName from "./components/ComponentName";
```

`./components` represents the component location, which in our case is the `components` subfolder.

Import statements like this should be added right before the component decleration, that means right above `export default` inside the `<script>` element.

## Parent component
```html
<template>
  <!-- attributes must be kebab-case -->
  <BlogPost post-title="hello!" />
</template>
<script>
import BlogPost from '@/components/BlogPost.vue';

export default {
  components: { BlogPost }
}
</script>
```

Notice that props with names in camelCase (with uppercase letters) must be used in kebab-case in the parent component. 

# Excercise 3
## Populate todo item with text
We will use props for ToDoItem in place of slots. 

:pencil2: In the component `ToDoItem`, add props below name: 'ToDoItem'

It should look like this:

```js
props: ['text']
```

:pencil2: Print out the prop content in the `ToDoItem` template.

:pencil2: Go to App.vue. Modify `ToDoItem` components inside the template. Add the prop you just created for each `ToDoItem`. It should look like this:

```html
<ToDoItem text="Eat meat" />
```
Bonus: try to add more todo items!

[Exercise 2](/exercise-2/)
[Exercise 4](/exercise-4/)