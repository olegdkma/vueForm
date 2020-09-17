<template>
  <div id="app">

    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: black;


}
html{
  overflow: hidden;
}
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
@media (max-width: 1230px){
  html{
    overflow: auto;
  }

}

</style>
