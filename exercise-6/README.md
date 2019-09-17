# v-if
v-if is used to hide and show content in our templates. The directive/attribute functions somewhat as a normal if sentence, it evaluates any JavaScript expression and renders the component or element if the expression is true. 

The format is as follows:
```html
  <div v-if="true">This will be shown since true is true</div>
  <div v-if="false">This will be hidden since false is not true</div>
```

We can leverage data fields or computed values and use them as values for our v-if directives.

```html
<template>
  <div>
    <input type="checkbox" v-model="shouldShowText" />
    <p v-if="shouldShowText">
      This text will be hidden if checkbox is unchecked
    </p>
  </div>
</template>

<script>
export default {
  name: "HideableText",
  data: function() {
    return {
      shouldShowText: false
    }
  }
}
</script>
```

In this example, the first element (a checkbox) will modify the state of `shouldShowText`. `shouldShowText` is by default `false`, as defined in the data field. When the checkbox is clicked, `shouldShowText` alternates the state, and renders our paragraph with the `v-if` when set to `true`.

#### Edit Example 6.1 - Hideable text:
[![Edit Example 6.1 - Hideable text](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-hideable-text-hr78i?fontsize=14&module=%2Fsrc%2FHideableText.vue)


JavaScript also evaluates other data types as `true` or `false`, so we can replace our toggle with text strings or numbers, among other data types. 

Here's an example where we use a text string as a value for `v-if`:

```html
<template>
  <form>
    <input type="text" v-model="enteredText" />
    <button type="submit" v-if="enteredText">Submit</button>
  </form>
</template>

<script>
export default {
  name: "FormComponent",
  data: function() {
    return {
      enteredText: ""
    }
  }
}
</script>
```

#### Edit Example 6.2 - Dynamic submit:
[![Edit Example 6.2 - Dynamic submit](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/example-dynamic-submit-zwgnn?fontsize=14&module=%2Fsrc%2FDynamicSubmit.vue)

# Exercise 6
## Hide add button
We want to avoid adding empty items in our list. 

:pencil2: Add a `v-if` attribute to the "add" button, so that it's hidden until the user has entered anything in the `input` field.

[Exercise 5](/exercise-5/)
[Exercise 7](/exercise-7/)