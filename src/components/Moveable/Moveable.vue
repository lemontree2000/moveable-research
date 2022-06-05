<template>
  <div ref="moveableElement"></div>
</template>
<script lang="ts">
import VanillaMoveable, {
  MoveableOptions,
  EVENTS,
  PROPERTIES,
  METHODS,
} from "moveable";
import { isUndefined } from "@daybrush/utils";

const methods: Record<string, any> = {};

METHODS.forEach((name) => {
  methods[name] = function (this: any, ...args: any[]) {
    this.$_moveable[name](...args);
  };
});
const watch: Record<string, any> = {};

PROPERTIES.forEach((name) => {
  watch[name] = function (this: any, value: any) {
    console.log('change',value )
    this.$_moveable[name] = value;
  };
});
export default {
  name: "moveable",
  methods,
  props: PROPERTIES,
  watch,
  mounted(this: any) {
    const options: Partial<MoveableOptions> = {};
    const props = this.$props;
    PROPERTIES.forEach((name) => {
      const value = props[name];

      if (!isUndefined(value)) {
        (options as any)[name] = props[name];
      }
    });
    const refs = this.$refs;
    const moveableElement = refs.moveableElement;
    const moveableContainer = document.querySelector('.canvas-page') as HTMLElement
    const moveableBounds = {
      left: 0,
      top: 0,
      right: moveableContainer.clientWidth,
      bottom: moveableContainer.clientHeight
    }
    console.log(moveableBounds)
    const moveable = new VanillaMoveable(moveableContainer, {
      ...options,
      portalContainer: moveableElement,
      bounds: moveableBounds,
      snappable: true,
    });

    EVENTS.forEach((name) => {
      moveable.on(name as any, (e: any) => {
        this.$emit(name, { ...e });
      });
    });
    this.$_moveable = moveable;
  },
  beforeDestroy(this: any) {
    this.$_moveable.destroy();
  },
};
</script>
