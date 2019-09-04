<template>
  <div id="app">
    <div class="headline">
      <h1>Border Radius Previewer</h1>
      <p>With VueJS</p>
    </div>
    <borderWrapper
      @border-list="borderList"
    />
    <div class="copy-wrapper">
      <p>border-radius: </p>
      <div id="copy-contents" class="copy-content">
        <copyWrapper
          :radiusList="this.border"
        />
      </div>
      <button @click="copy">COPY</button>
    </div>
  </div>
</template>

<script>
import borderWrapper from './components/BorderWrapper';
import copyWrapper from './components/CopyWrapper';
export default {
  name: 'app',
  components: {
    borderWrapper,
    copyWrapper
  },
  data(){
    return {
      border: {}
    }
  },
  methods: {
    borderList: function(e){
      return this.border = e;
    },
    copy: function(){
      const copyText = document.getElementById('copy-contents').textContent;
      const textArea = document.createElement('textarea');
      textArea.textContent = copyText;
      document.body.append(textArea);
      textArea.select();
      document.execCommand("copy");
      document.body.removeChild(textArea);
    },
  },
  computed: {
  }
}
</script>

<style lang="scss">
html {
  background-color: rgb(130, 171, 209);
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.demo-wrapper {
  display: grid;
  grid-template-columns: 100px repeat(4, 1fr) 100px;
  grid-template-rows: 100px repeat(4, 1fr) 100px;
  grid-template-areas:
    ". top-left top-left top-right top-right ."
    "left-top center center center center right-top"
    "left-top center center center center right-top"    
    "left-bottom center center center center right-bottom"
    "left-bottom center center center center right-bottom"
    ". bottom-left bottom-left bottom-right bottom-right .";
    width: 65vmin;
    height: 65vmin;
    margin: auto;
    justify-items: center;
    align-items: center;
    grid-gap: 3px;
}

.demo-component {
  grid-area: center;
  width: 50vmin;
  height: 50vmin;
  background-color: blueviolet;
  justify-self: center;
  align-self: center;
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

.copy-wrapper {
  display: flex;
  align-items: stretch;
  justify-content: center;
  margin-top: 2em;
}

p {
  font-size: 1.5rem;
  font-weight: bold;
  align-self: center;
}

.copy-content {
  align-self: center;
  font-size: 1.3rem;
  padding: 25px 10px;
  background-color: #2c3e50;
}

input[type="range"] {
  // overflow: hidden;
  background-color: blue;
  -webkit-appearance: none;
  height: 5px;
}
</style>
