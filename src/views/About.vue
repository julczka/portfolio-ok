<template>
  <div class="about">
    <h1>About me</h1>
    <div class="about-row">
      <div class="about-col col1">
        <div class="about-col__img"></div>
        <div class="about-col__socico">
          <a href="https://github.com/julczka" target="_blank"
            ><i class="fab fa-github "></i
          ></a>
          <a href="https://www.instagram.com/julczka/" target="_blank"
            ><i class="fab fa-instagram"></i
          ></a>
          <a
            href="https://www.linkedin.com/in/julia-gruszczynska"
            target="_blank"
            ><i class="fab fa-linkedin"></i
          ></a>
        </div>
        <div class="about-col__cv">
          <a href="mailto:julia.gru@gmail.com?subject=Hello"
            ><button class="button">Contact me</button></a
          >
        </div>
      </div>
      <div class="about-col col2">
        <div class="about-col__text">
          <h4>My name is <b>Julia Gruszczynska</b></h4>
          <h5>
            I’m a television director and beginner front-end developer.
            <b>Want to know my story? </b>Turn on the audio and press play.
          </h5>
        </div>
        <div class="youtube">
          <video-player :options="videoOptions" />
        </div>
        <button class="button">Download CV</button>
      </div>
    </div>

    <h2>What I can do for you</h2>
    <SkillsGrid id="skills" />

    <h2 id="resume">What I was doing untill now</h2>
    <TimelineDetection />
    <div class="fill"></div>
  </div>
</template>

<script>
import SkillsGrid from "../components/SkillsGrid";
import VideoPlayer from "../components/VideoPlayer";
import TimelineDetection from "../components/TimelineDetection";

export default {
  components: {
    SkillsGrid: SkillsGrid,
    VideoPlayer,
    TimelineDetection,
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
          huge: 900,
        },
        sources: [
          {
            src: require("../assets/julia_krysytyna_gruszczynska.mp4"),
            type: "video/mp4",
          },
        ],
      },
    };
  },

  methods: {
    playing() {
      console.log(" we are watching!!!");
    },
  },

  mounted() {},
};
</script>

<style lang="scss" scoped>
.fill {
  height: 400px;
}
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
  h2 {
    color: var(--bg-secondary);
    margin: 0.7em 1.6em;
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

  .fab:hover {
    -webkit-animation: jello-horizontal 0.9s both;
    animation: jello-horizontal 0.9s both;
  }
}

@import "../styles/_jello-keyframes.scss";

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

@media only screen and (max-width: 768px) {
  .about-row {
    flex-direction: column;
    width: 100%;

    h4 {
      text-align: center;
    }
  }

  .about-col {
    width: 90%;
    &__text {
      padding: 0em 0 2em 0;
      text-align: center;
      h4 {
        font-size: 2.2rem;
      }
      h5 {
        font-size: 2rem;
      }
    }
  }

  .youtube {
    width: 100%;
  }

  .col1,
  .col2 {
    padding: 0 0 2em 0;
  }

  .col2 {
    align-items: center;
  }
}
</style>
