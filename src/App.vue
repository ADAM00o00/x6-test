<script setup lang="ts">
import {onMounted} from "vue";
import {Graph} from "@antv/x6";
import {register, getTeleport} from "@antv/x6-vue-shape";
import CustomNode_Vue from "@/components/CustomNode_Vue.vue";

register({
  shape: 'custom-vue-node',
  width: 100,
  height: 100,
  component: CustomNode_Vue
})
const TeleportContainer = getTeleport();
onMounted(() => {
  const graph = new Graph(({
    container: document.getElementById('graph-container'),
    // autoResize:true,
    background: {
      color: '#F2F7FA'
    },
    panning: true,
  }))
  graph.addNode({
    shape:'custom-vue-node',
    x:100,
    y:60,
    data:{
      data:'测试节点1'
    }
  });
  graph.addNode({
    shape:'custom-vue-node',
    x:-100,
    y:-60,
    data:{
      data:'测试节点2'
    }
  })
  graph.centerContent();
})
</script>

<template>
  <div class="app-container">
    <div style="width: 100%;height: 100%" id="listener">
      <div id="graph-container" style="height: 100%"></div>
    </div>
    <TeleportContainer/>
  </div>
</template>

<style scoped>
.app-container {
  width: 100vw;
  height: 100vh;
}

.graph-parent {
  width: 100%;
  height: 500px;
  background-color: aqua;
}
</style>
