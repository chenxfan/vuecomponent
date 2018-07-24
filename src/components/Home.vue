<template>
  <div id="home" style="border: solid;">
    首页组件
    <br>
    <button @click='emitNews()'>给header组件广播数据</button>
  </div>
</template>
<script>
/*


*/

import VueEvent from '../model/VueEvent.js'
export default {
  data() {
    return {
      msg: '我是一个home组件',
      data: '给header组件的广播数据'
    }
  },
  methods: {

    run(data) {

      alert('我是Home组件的run方法' + data);
    },
    emitNews() {
      VueEvent.$emit('to-header', this.data)
    }
  },
  mounted() {
    VueEvent.$on('to-home', function(data) {
      console.log(data)
    })
  }


}

</script>
