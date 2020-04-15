<template>
  <div class="tl-container">
    <TimelineVertical v-if="detectMob" />
    <Timeline v-else />
  </div>
</template>

<script>
import Timeline from "../components/Timeline";
import TimelineVertical from "../components/TimelineVertical";
export default {
  components: {
    Timeline,
    TimelineVertical
  },
  computed: {
    detectMob: function() {
      return window.innerWidth <= 800 && window.innerHeight <= 600;
    }
  }
};
</script>

<style lang="scss" scoped>
.tl-container {
  width: 100%;
}
</style>
