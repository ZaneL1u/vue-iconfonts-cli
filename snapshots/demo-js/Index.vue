<template>
  <component :is="name" :size="size" :color="color" :style="style"></component>
</template>
<script>
/* eslint-disable */
import TabbarMy from './TabbarMy.vue';
import TabbarLove from './TabbarLove.vue';
import TabbarTodolist from './TabbarTodolist.vue';

export default {
  name:"iconfont",
  props:{
    name:{
      type: String,
      default: ""
    },
    size:{
      type: Number,
      default: #size#,
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
  components:{
    TabbarMy,
TabbarLove,
TabbarTodolist
  },
}
</script>
