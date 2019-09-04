<template>
    <div>
      <percentDisplay :percent="radiusList[0].radiusValue"/>
      <percentDisplay :percent="radiusList[1].radiusValue"/>
      <percentDisplay :percent="radiusList[3].radiusValue"/>
      <percentDisplay :percent="radiusList[5].radiusValue"/>
      <span style="color:white;">/</span>
      <percentDisplay :percent="radiusList[7].radiusValue"/>
      <percentDisplay :percent="radiusList[2].radiusValue"/>
      <percentDisplay :percent="radiusList[4].radiusValue"/>
      <percentDisplay :percent="radiusList[6].radiusValue"/>
    </div>
</template>
<script>
import percentDisplay from './PercentDisplay';
export default {
  name: 'copywrapper',
  components: {
    percentDisplay
  },
  props: {
    radiusList: [Array, Object]
  }
}
</script>