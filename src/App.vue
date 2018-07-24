<template>
  <div style="border: solid;">
    <h1>{{ msg }}</h1>
    <br/>
    <br/>
    <v-header ref='head' :title='title' :run='run' :all='this'></v-header>
<br>
<br>
    <v-home></v-home>
    <br>
    <br>
    <button v-on:click="getApp()">父组件调用子组件的方法和参数</button>
    <br/>
    <br/>
  </div>
</template>
<script>

import head from './components/Header.vue'
import home from './components/Home.vue'

export default {
  data() {
    return {
      msg: '根组件',
      title: '父组件title'
    }
  },
  methods: {
    run() {
      alert("父组件方法")
    },
    getApp() {
      this.$refs.head.runApp();
    }

  },
  components: {
    'v-header': head,
    'v-home':home,
  }
}

</script>
<style>


</style>
