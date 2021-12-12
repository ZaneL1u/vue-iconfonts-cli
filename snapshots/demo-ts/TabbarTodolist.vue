<template>
    <svg viewBox="0 0 1024 1024" :width="size" :height="size" :style="style">
      <path
        d="M570.88 268.8H145.92v640a77.0304 77.0304 0 0 0 76.8 76.8h424.96V345.6a77.0304 77.0304 0 0 0-76.8-76.8z"
        :fill="getIconColor(color, 0, '#EE7C3D')"
      />
      <path
        d="M796.16 120.32v783.36H227.84V120.32h568.32m5.12-81.92H222.72a77.0304 77.0304 0 0 0-76.8 76.8v793.6a77.0304 77.0304 0 0 0 76.8 76.8h578.56a77.0304 77.0304 0 0 0 76.8-76.8V115.2a77.0304 77.0304 0 0 0-76.8-76.8z"
        :fill="getIconColor(color, 1, '#333333')"
      />
      <path
        d="M673.28 309.76H350.72a40.96 40.96 0 0 1 0-81.92h322.56a40.96 40.96 0 0 1 0 81.92zM673.28 509.44H350.72a40.96 40.96 0 0 1 0-81.92h322.56a40.96 40.96 0 0 1 0 81.92zM468.7104 864.1024a40.96 40.96 0 0 1-28.9536-11.9808l-91.0848-91.0848a40.96 40.96 0 1 1 57.9072-57.9328l62.1312 62.1312 167.4496-167.4752a40.96 40.96 0 0 1 57.9328 57.9328l-196.4032 196.4288a40.96 40.96 0 0 1-28.9792 11.9808z"
        :fill="getIconColor(color, 2, '#333333')"
      />
    </svg>
</template>
<script>
import { getIconColor } from "./helper";

export default {
  name: "TabbarTodolist",
  props: {
    size: {
      type: Number,
      default: 18,
    },
    color: {
      type: String,
      default: "",
    },
    style: {
      type: String,
      default: "display: block;",
    },
  },
  methods: {
    getIconColor: getIconColor,
  },
};
</script>
