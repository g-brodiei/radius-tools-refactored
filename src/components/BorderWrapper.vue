<template>
  <div class="demo-wrapper">
    <div class="demo-component" :style="monitorBorder"></div>
    <radiusInput
      v-for="(radius, index) in radiusLists"
      :key="index"
      :radius="radius"
      @radius-data="updateRadius"
    />
  </div>
</template>

<script>
import radiusInput from "./InputWrapper";

export default {
  components: {
    radiusInput
  },
  data(){
    return {
      radiusLists: [
        {
          name: 'topLeft',
          radiusValue: 50,
          areaName: 'top-left'
        },
        {
          name: 'topRight',
          radiusValue: 50,
          areaName: 'top-right'
        },
        {
          name: 'rightTop',
          radiusValue: 50,
          areaName: 'right-top',
          rotateDeg: 90
        },
        {
          name: 'rightBottom',
          radiusValue: 50,
          areaName: 'right-bottom',
          rotateDeg: 90
        },
        {
          name: 'bottomRight',
          radiusValue: 50,
          areaName: 'bottom-right'
        },
        {
          name: 'bottomLeft',
          radiusValue: 50,
          areaName: 'bottom-left'
        },
        {
          name: 'leftBottom',
          radiusValue: 50,
          areaName: 'left-bottom',
          rotateDeg: -90
        },
        {
          name: 'leftTop',
          radiusValue: 50,
          areaName: 'left-top',
          rotateDeg: -90
        }
      ]
    }
  },
  methods: {
    updateRadius: function(e){
      for(var i in this.radiusLists){
        if(this.radiusLists[i].name == e.name){
          this.radiusLists[i].radiusValue = e.radiusValue;
          break;
        }
      }
    }
  },
  computed: {
    monitorBorder: function(){
      let tL = this.radiusLists.find((obj)=>{
       return obj.name == 'topLeft';
      }).radiusValue;

      let tR = this.radiusLists.find((obj)=>{
       return obj.name == 'topRight';
      }).radiusValue;

      let rT = this.radiusLists.find((obj)=>{
       return obj.name == 'rightTop';
      }).radiusValue;

      let rB = this.radiusLists.find((obj)=>{
       return obj.name == 'rightBottom';
      }).radiusValue;

      let bR = this.radiusLists.find((obj)=>{
       return obj.name == 'bottomRight';
      }).radiusValue;

      let bL = this.radiusLists.find((obj)=>{
       return obj.name == 'bottomLeft';
      }).radiusValue;

      let lB = this.radiusLists.find((obj)=>{
       return obj.name == 'leftBottom';
      }).radiusValue;
      
      let lT = this.radiusLists.find((obj)=>{
       return obj.name == 'leftTop';
      }).radiusValue;

      const borderTL = String(tL+ '%' + " " + lT + '%');
      const borderTR = String(tR + '%' + " " + rT + '%');
      const borderBR = String(bR + '%' + " " + rB + '%');
      const borderBL = String(bL + '%' + " " + lB + '%');
      
      const styleObject = {
        'border-top-left-radius': borderTL,
        'border-top-right-radius': borderTR,
        'border-bottom-right-radius': borderBR,
        'border-bottom-left-radius': borderBL
      };

      return styleObject;
    }
  }
}
</script>

<style lang="scss">
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

  .right-top, .right-bottom {
    input[type="range"]{
      transform: rotate(90deg);
    }
  }
  .left-top, .left-bottom {
    input[type="range"]{
      transform: rotate(-90deg);
    }
  }

  .right-bottom, .bottom-right, .top-right, .left-top {
    direction: rtl;
  }
</style>