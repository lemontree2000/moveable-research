<script lang="ts">
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
  setup() {

  },
})
</script>


<template>
  <section class="left">
    <!-- <section class="sidebar"></section> -->
    <section class="sidebar-drawer">
      <section class="component-item">容器</section>
    </section>
  </section>
</template>



<style lang="scss">
.component-item {
  width: 100px;
  height: 50px;
  border: 1px solid #dedede;
  text-align: center;
  line-height: 50px;
  cursor: pointer;
}
</style>