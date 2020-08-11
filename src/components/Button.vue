<template>
  <div>
    <button :class="type + ' ' + size" :style="style" @click="$emit('click')">{{text}}</button>
  </div>
</template>

<script>
export default {
  name: "v-button",
  props: {
    text: { type: String, default: "click me" },
    type: { type: String, default: "normal" }, // values: normal, rounded, outlined, text, tile
    size: { type: String, default: "default" }, // values: xsmall, small, default, large, xlarge
    color: { type: String, default: "#42b983" },
  },
  computed: {
    style() {
      var style = "";
      if (
        this.type === "normal" ||
        this.type === "rounded" ||
        this.type === "tile"
      ) {
        style = "background-color: " + this.color + " !important";
      } else {
        style =
          "border-color: " +
          this.color +
          " !important; color: " +
          this.color +
          " !important";
      }
      return style;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  display: inline-block;
}

div > button {
  border: none;
  font-weight: bold;
  align-items: center;
  border-radius: 4px;
  cursor: pointer;
  color: white;
  display: inline-flex;
  flex: 0 0 auto;
  font-weight: 500;
  letter-spacing: 0.0892857143em;
  justify-content: center;
  margin: 5px;
  outline: 0;
  padding: 10px;
  position: relative;
  text-decoration: none;
  text-indent: 0.0892857143em;
  text-transform: uppercase;
  transition-duration: 0.28s;
  transition-property: box-shadow, transform, opacity;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  vertical-align: middle;
  white-space: nowrap;
}

div > button:hover {
  opacity: 0.8;
  transition-duration: 0.28s;
  transition-property: box-shadow, transform, opacity;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

.xsmall {
  font-size: 0.625rem;
  height: 28px;
  min-width: 40px;
}

.small {
  font-size: 0.75rem;
  height: 32px;
  min-width: 65px;
}

.default {
  font-size: 0.825rem;
  height: 38px;
  min-width: 80px;
}

.large {
  font-size: 0.875rem;
  height: 44px;
  min-width: 100px;
}

.xlarge {
  font-size: 1rem;
  height: 50px;
  min-width: 120px;
}

.outlined {
  background-color: white !important;
  color: #42b983;
  border: 1px solid #42b983 !important;
}

.outlined:hover {
  background-color: #f6fffb !important;
}

.rounded {
  border-radius: 20px;
}

.text {
  background-color: white !important;
  color: #42b983;
}

.text:hover {
  background-color: #f6fffb !important;
}

.tile {
  border-radius: 0;
}
</style>
