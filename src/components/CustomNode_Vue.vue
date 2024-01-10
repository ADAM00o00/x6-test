<script setup lang="ts">
import {inject, onMounted, ref} from "vue";
import {Node} from "@antv/x6"
interface NodeData{
  data:string;
}
const getNode: (() => Node) | undefined = inject('getNode');
const nodeData = ref<undefined | NodeData>(undefined);
onMounted(()=>{
  const node = getNode() as  Node;
  nodeData.value=node.getData() as NodeData;
})
</script>

<template>
{{nodeData?.data}}
</template>

<style scoped>

</style>