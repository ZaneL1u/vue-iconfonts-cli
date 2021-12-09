<template>
  <component :is="name"></component>
</template>
<script>
/* eslint-disable */
import IconTabbarMy from "./IconTabbarMy";
import IconTabbarLove from "./IconTabbarLove";
import IconTabbarTodolist from "./IconTabbarTodolist";
export default {
  name: "iconfont",
  props: {
    name: {
      type: String,
      default: "",
    },
  },
  componetns: {
    IconTabbarMy,
    IconTabbarLove,
    IconTabbarTodolist,
  },
};
</script>
