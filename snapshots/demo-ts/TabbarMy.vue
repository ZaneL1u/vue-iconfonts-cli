<template>
  <div :style="renderSVG()"></div>
</template>
<script>
import { getIconColor } from "./helper";
import { svg2css } from "./svg2css";

export default {
  name: "TabbarMy",
  props: {
    size: {
      type: Number,
      default: 18,
    },
    color: {
      type: Object,
      default: "",
    },
    style: {
      type: [String, Object],
      default: "display: block;",
    },
  },
  methods: {
    renderSVG:function(){
      const res = svg2css(`
    <svg viewBox="0 0 1024 1024" width="${this.size}" height="${this.size}" style="${this.style}">
      <path
        d="M373.76 241.28a245.3248 245.3248 0 0 0-90.368 17.152 245.888 245.888 0 0 0 318.976 318.976A245.888 245.888 0 0 0 373.76 241.28z"
        fill="${getIconColor(this.color, 0, '#EE7C3D')}"
      />
      <path
        d="M921.1392 873.6768a411.9552 411.9552 0 0 0-255.872-332.8 245.76 245.76 0 1 0-306.5344 0 411.9552 411.9552 0 0 0-255.872 332.8 42.24 42.24 0 1 0 83.8656 10.0352 327.68 327.68 0 0 1 556.9792-192 323.6864 323.6864 0 0 1 93.568 192 42.24 42.24 0 1 0 83.8656-10.0864zM348.16 348.8a163.84 163.84 0 1 1 181.0176 162.944 382.83008 382.83008 0 0 0-34.3552 0A164.096 164.096 0 0 1 348.16 348.8z"
        fill="${getIconColor(this.color, 1, '#333333')}"
      />
    </svg>
`,this.color);
      return `background-image: url("${res}");width:${this.size}px;height:${this.size}px;${this.style}`;
    }
  },
};
</script>
