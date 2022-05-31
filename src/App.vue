<template>
  <div class="root">
    <div class="header">header</div>
    <div class="body">
      <!-- <button @click="toggleDraggable">Toggle {{ draggable }}</button> -->
      <!-- <editor-left /> -->
      <editor-core />
      <!-- <editor-right /> -->
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from '@vue/composition-api';
import EditorLeft from "./components/EditorLeft/index.vue";
import EditorRight from "./components/EditorRight/index.vue";
import EditorCore from "./components/EditorCore/index.vue";

export default defineComponent({
  components: {
    EditorLeft,
    EditorCore,
    EditorRight
  },
  setup() {}
});
</script>
<style>
html,
body {
  /* position: relative; */
  height: 100%;
  margin: 0;
  padding: 0;
}

.root {
  /* position: relative; */
  display: flex;
  height: 100%;
  flex-direction: column;
}

.container {
  /* position: relative; */
  display: flex;
  flex: 1;
  align-items: center;
  justify-content: center;
  /* margin-top: 50px; */
}
.canvas-content {
  width: 790px;
}
.canvas-page {
  border: 1px solid #353535;
  min-height: 800px;
  position: relative;
}

.target {
  position: absolute;
  width: 100px;
  height: 100px;
  top: 150px;
  left: 100px;
  line-height: 100px;
  text-align: center;
  background: #ee8;
  color: #333;
  font-weight: bold;
  border: 1px solid #333;
  box-sizing: border-box;
}

.header {
  height: 50px;
  background: #353535;
  text-align: center;
  line-height: 50px;
  color: #fff;
}
.body {
  display: flex;
  height: 100%;
}

.left,
.right {
  display: flex;
  width: 280px;
  border: 1px solid #333;
}

.sidebar {
  width: 50px;
}
.sidebar-drawer {
  width: 230px;
  border-left: 1px solid #333;
}
</style>
