<template>
  <span>
    {{percent}}%
    <slot></slot>
  </span>
</template>
<script>
import { isString } from 'util';
export default {
  name: 'percentdisplay',
  props: ['percent'],
  computed: {
    addPercent: function(){
      if (isString(this.percent) == true) {
        return this.percent + "%";
      } else {
        return this.percent = "/";
      }
    }
  }
}
</script>
<style scoped>
  span {
    color: white;
  }
</style>