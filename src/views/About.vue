<template>
  <div class="about">
    <h1>About me</h1>
    <div class="youtube">
      <video-player class="vjs-layout-medium" :options="videoOptions" />
      <!-- <youtube
        :video-id="videoId"
        :player-vars="playerVars"
        @playing="playing"
      ></youtube> -->
    </div>
    <div class="fill"></div>
    <SkillsGrid />
    <div class="fill"></div>
  </div>
</template>

<script>
import SkillsGrid from "../components/SkillsGrid";
import VideoPlayer from "../components/VideoPlayer";
export default {
  components: {
    SkillsGrid: SkillsGrid,
    VideoPlayer
  },
  data() {
    return {
      videoOptions: {
        autoplay: true,
        controls: true,
        fluid: true,
        responsive: true,
        breakpoints: {
          tiny: 300,
          xsmall: 400,
          small: 500,
          medium: 600,
          large: 700,
          xlarge: 800,
          huge: 900
        },
        sources: [
          {
            src: require("../assets/julia_krysytyna_gruszczynska.mp4"),
            type: "video/mp4"
          }
        ]
      }
      // videoId: "7AXsVXHfir0",
      // playerVars: {
      //   autoplay: 0,
      //   showinfo: 0,
      //   modestbranding: 1,
      //   controls: 1,
      //   rel: 0,
      //   loop: 1
      // }
    };
  },

  methods: {
    playing() {
      console.log(" we are watching!!!");
    }
  },

  mounted() {}
};
</script>

<style lang="scss" scoped>
// @import "@/styles/_video.scss";
// $pink-light-hex: #f23558;
.fill {
  height: 200px;
}
</style>
