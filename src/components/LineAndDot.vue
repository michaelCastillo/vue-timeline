<template>
  <div class="linesAndDotsContainer">
    <div class="lineDot">
      <div class="line" />
    </div>
    <div class="lineDot">
      <div v-bind:class="['dot',`dot-${index}`, {selected: selected}]" />
    </div>
    <div class="lineDot">
      <div class="line" />
    </div>
  </div>
</template>

<script>
export default {
  name: "LineAndDot",
  props: {
    data: Array,
    index: Number,
    selected: Boolean
  },
  mounted: function() {
    const tester = document.querySelector(`.dot-${this.index}`);
    const raf =
      window.requestAnimationFrame ||
      window.webkitRequestAnimationFrame ||
      window.mozRequestAnimationFrame ||
      function(callback) {
        window.setTimeout(callback, 1000 / 60);
      };
    const handler = () =>
      raf(() => {
        if(this.isInView(tester)){
          this.$emit("send-message", this.index);
        }
      });
    window.addEventListener("scroll", handler);
  },
  methods: {
    isInView: function(el) {
      const scroll = window.scrollY || window.pageYOffset;
      const boundsTop = el.getBoundingClientRect().top + scroll;

      const viewport = {
        top: scroll,
        bottom: scroll + window.innerHeight -350
      };
      const bounds = {
        top: boundsTop,
        bottom: boundsTop + el.clientHeight
      };
      return (
        (bounds.bottom >= viewport.top && bounds.bottom <= viewport.bottom) ||
        (bounds.top <= viewport.bottom && bounds.top >= viewport.top)
      );
    }
  }
};
</script>

<style scoped>
.lineDot {
  display: flex;
  flex:1;
  width: 100%;
  flex-grow: 1;
  justify-content: center;
}
.linesAndDotsContainer {
  margin: 0px 36px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.line {
  height: 200px;
  width: 4px;
  background-color: black;
}
.dot {
  height: 32px;
  width: 32px;
  border-radius: 50%;
  background-color: black;
}
.selected{
  background-color: yellow;
}
</style>
