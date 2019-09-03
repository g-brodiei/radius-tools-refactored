<template>
  <div class="input-wrapper" :class="this.radius.areaName">
    <input 
      type="range" 
      min="0" 
      max="100"
      v-model="dataName"
      @change="emitRadiusData"
      />
  </div>
</template>
<script>
export default {
  name: 'radius-input',
  props: {
          radius: Object
          },
  data() {
    return {
      dataName: "",
    }
  },
  methods: {
    emitRadiusData: function(){
      let tempObject = {};
      tempObject['name'] = this.radius.name;
      tempObject['radiusValue'] = this.dataName;
      this.$emit('radius-data', tempObject);
    }
  },
  computed: {
    getGridArea: function(){
      return {
        'grid-area': this.radius.areaName,
        'transform': 'rotate('+this.radius.rotateDeg+'deg)'
      };
    }
  }
}
</script>
<style lang="scss" scoped>
  input[type="range"] {
    // overflow: hidden;
    background-color: blue;
    -webkit-appearance: none;
    height: 5px;
  }
  .top-left {
    grid-area: top-left;
  }

  .top-right {
    grid-area: top-right;
  }

  .right-top {
    grid-area: right-top;
  }

  .right-bottom {
    grid-area: right-bottom;
  }

  .bottom-right {
    grid-area: bottom-right;
  }

  .bottom-left {
    grid-area: bottom-left;
  }

  .left-bottom {
    grid-area: left-bottom;
  }

  .left-top {
    grid-area: left-top;
  }
</style>