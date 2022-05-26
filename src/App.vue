<template>
  <div class="root">
    <div class="container">
      <div class="row"></div>
      <div class="target" ref="target">Target</div>
      <div class="target" ref="target">Target</div>
      <span class="abc">Target</span>
      <button @click="toggleDraggable">Toggle {{ draggable }}</button>
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
    </div>
  </div>
</template>
<script>
import Moveable from "./components/Moveable/Moveable.vue";

export default {
  components: {
    Moveable,
  },
  data() {
    return {
      draggable: true,
      dragTarget: null,
    };
  },
  mounted() {
    console.log(this);
  },
  methods: {
    onDrag(e) {
      e.target.style.transform = e.transform;
    },
    toggleDraggable() {
      this.draggable = !this.draggable;
    },
  },
};
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
.row {
  width: 100px;
  height: 100px;
  background-color: #333;
}
.root {
  position: relative;
}

.container {
  position: relative;
  margin-top: 50px;
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

.target1 {
  left: 120px;
  top: 120px;
}

.target2 {
  left: 300px;
  top: 140px;
}

.target3 {
  left: 180px;
  top: 250px;
}
</style>
