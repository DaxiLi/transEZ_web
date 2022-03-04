<template>
  <div id="app">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
<!--    <Passwd></Passwd>-->
    <Header></Header>
<!--    <Index></Index>-->
    <Board></Board>
    <Footer></Footer>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Passwd from "@/components/Passwd";
import Footer from "@/components/Footer"
// import Index from "@/components/Index"
import Header from "@/components/Header";
import Board from "@/components/Board";


export default {
  name: 'App',
  components: {
    Board,
    Header,
    Footer,
    // HelloWorld,
    // Passwd
    // Index
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
  /*margin-top: 60px;*/
  /*height: 100vh;*/
  /*width: 100vw;*/
  /*position: absolute;*/
}
</style>
