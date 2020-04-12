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
    <h1>What I can do for you</h1>
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
        autoplay: false,
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
.about {
  width: 100%;

  @include flex-center();
  flex-direction: column;
}
.youtube {
  width: 50%;
}
.fill {
  height: 200px;
}
</style>
