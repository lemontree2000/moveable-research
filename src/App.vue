<template>
  <div class="root">
    <div class="header">header</div>
    <div class="body">
      <!-- <button @click="toggleDraggable">Toggle {{ draggable }}</button> -->
      <section class="left">
        <section class="sidebar"></section>
        <section class="sidebar-drawer"></section>
      </section>
      <div class="container">
        <section class="canvas-content">
          <section class="canvas-page">
            <div class="target" ref="target">Target</div>
            <div class="target" ref="target">Target</div>
            <moveable
              target=".target"
              v-bind:draggable="draggable"
              v-bind:throttleDrag="1"
              v-bind:edgeDraggable="false"
              v-bind:startDragRotate="0"
              v-bind:throttleDragRotate="0"
              v-bind:individualGroupable="true"
              @drag="onDrag"
            />
          </section>
        </section>
      </div>
      <div class="right">right</div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api';
import { OnDrag } from 'moveable';
import Moveable from "./components/Moveable/Moveable.vue";

export default defineComponent({
  components: {
    Moveable,
  },
  setup() {
    const draggable = ref(true)

    const toggleDraggable = () => {
      draggable.value = !draggable.value;
    }

    const onDrag = (e: OnDrag) => {
      e.target.style.transform = e.transform;
    }

    return {
      draggable,
      toggleDraggable,
      onDrag,
    }
  }
});
</script>
<style>
html,
body {
  position: relative;
  height: 100%;
  margin: 0;
  padding: 0;
}

.description {
  padding: 10px;
}
.root {
  position: relative;
  display: flex;
  height: 100%;
  flex-direction: column;
}

.container {
  position: relative;
  display: flex;
  flex: 1;
  align-items: center;
  justify-content: center
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
