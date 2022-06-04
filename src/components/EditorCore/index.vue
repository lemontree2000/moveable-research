<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api'
import { OnDrag } from 'moveable';
import Moveable from "../Moveable/Moveable.vue";

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
  },
})
</script>


<template>
  <div class="container">
    <section class="canvas-content">
      <section class="canvas-page">
        <div class="target" ref="target">Target</div>
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
</template>


<style lang="sass">
.wrapper
  display: flex
  div
    width: 100px
    height: 100px
    background: #dedede
    border: 1px solid red
</style>