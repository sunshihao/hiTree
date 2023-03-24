<template>
  <!-- 虚拟滚动还是需要高度的 -->
  <DraggableTree v-model="data2" virtualization ref="tree3" style="height: 100vh;width: 300px;" :defaultOpen="true">
    <template #default="{ node, stat }">
      <div class="home_card">
        <a class="home_card_in">
          <span v-if="stat.children.length" @click="stat.open = !stat.open">
            {{ stat.open ? "-" : "+" }}
          </span>
          {{ node.text }}
        </a>
      </div>
    </template>
  </DraggableTree>
</template>

<script lang="ts" setup>
import {
  ref
} from "vue";

import DraggableTree from "./components/DraggableTree";
import data0 from "./table.json";
import * as hp from "./utils/helper";

const data2 = ref([...hp.cloneObject(data0)]);
</script>

<style scoped>
.home {
  background-color: azure;
  height: 400px;
  width: 600px;
  overflow: auto;
}

.home_card {
  margin-top: 2px;
  height: 34px;
  font-size: 14px;
}

.home_card_in {
  border: 1px solid #777;
  border-radius: 4px;
  padding: 4px;
}

.home_card_tz {
  display: none;
}

.home_card_tz :hover {
  display: block;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
