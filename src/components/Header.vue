<template>
  <div style="border: solid;">
    {{msg}}
    <br> {{title}}
    <button @click='getParents()'>点击执行父组件方法</button>
    <br>
    <br>
    <button @click='emitHome'>给home组件广播数据</button>
  </div>
</template>
<script>
import VueEvent from '../model/VueEvent.js'
export default {
  data() {
    return {
      msg: '头部组件',
      data: '给home组件的广播数据'
    }
  },
  methods: {
    getParents() {
      this.all.run();
      this.$parent.run();
    },
    runApp() {
      alert("子组件方法")
    },
    emitHome() {
      VueEvent.$emit('to-home', this.data)
    }
  },
  mounted() {
    VueEvent.$on('to-header', function(data) {
      console.log(data)
    })
  },
  props: ['title', 'run', 'all']
}

</script>
