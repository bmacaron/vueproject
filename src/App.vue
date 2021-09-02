<template>
  <div id="app">
    <header-component></header-component>
    <input-component></input-component>
    <list-component v-bind:list="myList"></list-component>
    <footer-component @clearItem="clearItem"></footer-component>
  </div>
</template>

<script>
import HeaderComponent from './components/Header-component.vue'
import FooterComponent from './components/Footer-component.vue'
import InputComponent from './components/Input-component.vue'
import ListComponent from './components/List-component.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    FooterComponent,
    InputComponent,
    ListComponent
  },
  data() {
    return {
      myList: []
    }
  },
  created() {
    if(localStorage.length !== "") {
      for(var i = 0; i < localStorage.length; i++) {
        var key = localStorage.key(i);
        if(key !== 'loglevel:webpack-dev-server') {
            var temp = localStorage.getItem(key);
          var item = JSON.parse(temp);
          if(item !== "") {
            this.myList.push(item);
          }
        }
      }
    }
  },
  methods : {
    clearItem() {
      this.myList = [];
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
