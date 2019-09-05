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
    <footerSection/>
  </div>
</template>

<script>
import borderWrapper from './components/BorderWrapper';
import copyWrapper from './components/CopyWrapper';
import footerSection from './components/Footer';
export default {
  name: 'app',
  components: {
    borderWrapper,
    copyWrapper,
    footerSection
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
  @media only screen and (max-width:1200px) {
    .demo-wrapper {
      grid-template-columns: 50px repeat(4, 1fr) 50px;
      grid-template-rows: 50px repeat(4, 1fr) 50px;
    }
  }
  @media only screen and (max-width:768px) {
    .demo-wrapper {
      grid-template-columns: 50px repeat(4, 1fr) 50px;
      grid-template-rows: 50px repeat(4, 1fr) 50px;
    }
  }
  @media only screen and (max-width:576px) {
    .demo-wrapper {
      grid-template-columns: 25px repeat(4, 1fr) 25px;
      grid-template-rows: 25px repeat(4, 1fr) 25px;
      width: 85vmin;
      height: 85min;
    }
  }
  @media only screen and (max-width:420px) {
    .demo-wrapper {
      grid-template-columns: 5px repeat(4, 1fr) 5px;
      grid-template-rows: 5px repeat(4, 1fr) 5px;
      width: 85vmin;
      height: 85vmin;
    }
  }
</style>
