# raidus-tools-refactored

>This is a beginner tier project practice base on the collection of [APP-IDEAS](https://github.com/florinpop17/app-ideas), thanks to florinpop17. Check project details [here](https://github.com/florinpop17/app-ideas/blob/master/Projects/Border-Radius-Previewer.md).

## Implementation and Learnings

components, breaking down html structure of radius tools into four components under App.vue:
- App.vue (grand parent)
  - BorderWrapper.vue (parent1)
    - InputWrapper.vue (child1)
  - CopyWrapper.vue (parent2)
    - PercentDisplay.vue (child2)

**TL;DR:** passing data from child to child, going through the hierarchy level of app structure. child1 > parent1 > grandparent > parent2 > child2.

### Listening to child events, and pass it to parent. (Send data upward)
#### Resource
> [VueJS - Listening-to-Child-Components-Events](https://vuejs.org/v2/guide/components.html#Listening-to-Child-Components-Events)

>[DOM event list](https://developer.mozilla.org/en-US/docs/Web/Events)

Using the $emit method to emit an event from the child component to its parent component. (e.g. send the data from InputWrapper back to BorderWrapper)

#### HOW

Assign an *$emit* method with a *v-on* DOM event *[see event list](https://developer.mozilla.org/en-US/docs/Web/Events)* (i.e. v-on:click, v-on:change etc), then listen to it on parent with the child method name with *v-on* .

```html
<parent>
    <div v-on:receiveName="function(object){}">
    </div>
</parent>

------------------------------------------------

<child v-on:click="$(emit).('receiveName', object)">
</child>
```

### Pass data to from parent to child. (Send data downwards)

>Resource [VueJS - Passing-Data-to-Child-Components-with-Props](https://vuejs.org/v2/guide/components.html#Passing-Data-to-Child-Components-with-Props)

Names of the *Props* is set on the child component to allow the parent to *v-bind* data and pass it downwards.

#### How

```html
<parent
  v-bind:nameMe="names"
>
</parent>

-------------------------------------------------

<child>
  <p>{{nameMe}}</p>
</child>

<script>
export default{
  // name your component
  name: 'chlid',

  // two formats for props, direct naming or set type of property being recevied.
  props: ['nameMe']

  // or
  props: {
    nameMe: String
  }
}
</script>

```
