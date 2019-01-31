<template>
  <div id="app">
    <section class="todoapp" id="todoapp">
      <Header></Header>
      <Todo></Todo>
      <!-- <Tabs></Tabs> -->
    </section>
    <Footer></Footer>
    <!-- <router-view/> -->
  </div>
</template>

<script>
import Header from "./components/header";
import Todo from "./components/todo";
// import Tabs from './components/tabs'
import Footer from './components/footer'
let id = 0;
export default {
  name: "App",
  components: {
    Header,
    Todo,
    Footer,
    // Tabs
  },
  data() {
    return {
     
    }
  }
};
</script>

<style>
</style>
