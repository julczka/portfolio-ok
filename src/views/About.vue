<template>
  <div class="about">
    <h1>About me</h1>
    <div class="about-row">
      <div class="about-col col1">
        <div class="about-col__img"></div>
        <div class="about-col__socico">
          <i class="fab fa-github"></i>
          <i class="fab fa-instagram"></i>
          <i class="fab fa-linkedin"></i>
        </div>
        <div class="about-col__cv">
          <button>Contact me</button>
        </div>
      </div>
      <div class="about-col col2">
        <div class="about-col__text">
          <h4>My name is Julia Gruszczynska</h4>
          <h5>
            I’m a television director and beginner front-end developer. Want to
            know my story? Press play.
          </h5>
        </div>
        <div class="youtube">
          <video-player class="vjs-layout-medium" :options="videoOptions" />
        </div>
        <button>Download CV</button>
      </div>
    </div>
    <h2>What I can do for you</h2>
    <SkillsGrid />
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
  justify-content: flex-start;
  h1 {
    font-size: 7rem;
  }
}

.about-row {
  @include flex-center();
  margin: 1rem 3rem 5rem 3rem;
  // height: calc(100vh - 18 rem);

  h4,
  h5 {
    text-align: left;
  }

  h4 {
    color: $pink-light-hex;
  }

  h5 {
    color: var(--text-secondary);
  }
}
.about-col {
  display: flex;

  flex-direction: column;

  height: 100%;
  width: 50%;

  &__img {
    border-radius: 200px;
    filter: grayscale(1);
    width: 23rem;
    height: 23rem;
    background-image: url("../assets/about-ME.jpg");
    background-size: cover;
    background-position: center;
  }

  i {
    font-size: 4rem;
    padding: 0.2em;
    color: $pink-light-hex;
  }

  &__text {
    padding: 0em 0 2em 0;
  }
}

.col1 {
  // flex: 1 1 20em;

  align-items: center;
  justify-content: space-between;
  padding-right: 3em;
}
.col2 {
  // flex: 1 2 20em;
  align-items: flex-start;
  justify-content: space-between;
  padding-left: 3em;

  button {
    align-self: flex-end;
    margin-right: calc(10%);
  }
}

.youtube {
  width: 90%;
}
.fill {
  height: 200px;
}
</style>
