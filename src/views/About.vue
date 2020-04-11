<template>
  <div class="about">
    <h1>About me</h1>
    <div class="fill"></div>
    <SkillsGrid />
    <div class="fill"></div>
  </div>
</template>

<script>
import SkillsGrid from "../components/SkillsGrid";
export default {
  components: {
    SkillsGrid: SkillsGrid
  },
  data() {
    return {};
  },

  methods: {},

  mounted() {}
};
</script>

<style lang="scss" scoped>
// @import "@/styles/_variables.scss";
// $pink-light-hex: #f23558;
.fill {
  height: 200px;
}
</style>
