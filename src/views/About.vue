<template>
  <div class="about">
    <h1>This is an about page</h1>

    <div class="filler"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // windowWidth: window.innerWidth,
      // windowHeight: window.innerHeight,
    };
  },

  methods: {},

  mounted() {
    // window.onresize = () => {
    //   this.windowWidth = window.innerWidth;
    //   this.windowHeight = window.innerHeight;
    //   if (this.windowWidth / this.windowHeight > 1) console.log("ratio > 1");
    //   else this.lol();
    // };
    // window.onresize = calculateRatio(windowWidth, windowHeight);
    // calculateRatio(this.windowWidth, this.windowHeight);
    // window.addEventListener("resize", () => {
    //   this.width = window.innerWidth;
    //   this.height = window.innerHeight;
    //   console.log(this.width);
    //   console.log(this.height);
    //   var ratio = this.widht / this.height;
    //   return ratio;
    // });
  },
};
</script>

<style lang="scss" scoped>
// @import "@/styles/_variables.scss";
// $pink-light-hex: #f23558;
.about {
  display: flex;
  align-items: flex-start;
  justify-content: center;
}

.filler {
  height: 6000px;
  width: 3px;
  opacity: 1;
  background-color: $pink-light-hex;
}
</style>
