<template>
  <div class="project_details">
    <div class="details-row">
      <div :class="isApp ? 'gallery-container-vertical' : 'gallery-container'">
        <div
          :class="isApp ? 'image-vertical' : 'image'"
          v-if="currentProject.videoSrc"
        >
          <iframe
            v-if="currentProject.videoSrc"
            :src="currentProject.videoSrc"
            frameborder="0"
            allow="autoplay; fullscreen"
            allowfullscreen
            width="100%"
            height="100%"
            style="position:absolute; top:0; left: 0;"
          ></iframe>
        </div>
        <img
          v-else
          :src="require(`../assets/${currentProject.imgCover}`)"
          alt=""
          srcset=""
          width="100%"
        />
      </div>

      <div class="text left ">
        <h1>{{ currentProject.projectTitle }}</h1>
        <h4>{{ currentProject.category }}</h4>
        <p>{{ currentProject.description }}</p>

        <h6>{{ currentProject.myRole }}</h6>

        <div class="button_wrapper">
          <a v-if="currentProject.pageLink" :href="currentProject.pageLink"
            ><button class="button">Live site</button></a
          >
          <router-link to="/Works">
            <button class="button">Back to works</button>
          </router-link>
        </div>
      </div>
    </div>

    <div class="details-row">
      <div class="carousel-container">
        <carousel
          :perPage="1"
          :autoplay="true"
          :loop="true"
          :navigationEnabled="true"
          :autoplayTimeout="3000"
          navigationNextLabel=">"
          navigationPrevLabel="<"
          paginationPosition="bottom-overlay"
          paginationActiveColor="#f23558"
        >
          <slide v-for="(image, index) in images" :key="index">
            <img
              :src="require(`../assets/${image}`)"
              alt=""
              srcset=""
              width="100%"
            />
          </slide>
        </carousel>
      </div>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from "vue-carousel";
import ProjectsVideo from "../data/projects-video.json";
import ProjectsCode from "../data/projects-code.json";
import ProjectsDesign from "../data/projects-design.json";

export default {
  components: {
    Carousel,
    Slide
  },

  computed: {
    isApp() {
      return this.$route.path === "/project/8";
    }
  },
  data() {
    return {
      projectId: this.$route.params.id,
      currentProject:
        ProjectsVideo.filter(p => p.id == this.$route.params.id).pop() ||
        ProjectsCode.filter(p => p.id == this.$route.params.id).pop() ||
        ProjectsDesign.filter(p => p.id == this.$route.params.id).pop(),
      images: this.$route.params.images
    };
  }
};
</script>

<style lang="scss" scoped>
.swiper-wrapper {
  height: 1000px;
}
.project_details {
  height: 100vh;

  margin-top: 5em;
}

.details-row {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 3em;
}

.gallery-container {
  width: 50%;
  margin: 0 2em 0 5em;
}

.gallery-container-vertical {
  width: 25%;
  margin: 0 2em 0 5em;
}

.carousel-container {
  width: 80%;
  margin: 5em 0;
  justify-content: center;
}

.image {
  overflow: hidden;
  width: 100%;
  padding-top: 56.25%;
  position: relative;
  display: block;
}

.image-vertical {
  overflow: hidden;
  width: 100%;

  padding-top: 177.77%;
  position: relative;
  display: block;
}

.text {
  width: 50%;
  height: 100%;
  margin: 0 4em 0 2em;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
}

.button_wrapper {
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-top: 1em;

  .button {
    margin: 0;
  }
}

p {
  font-family: futura-pt, sans-serif;
  color: var(--text-secondary);
  font-size: 1.2rem;
  text-align: justify;
  text-justify: inter-word;
}

.left {
  text-align: left;
}

@media screen and (max-aspect-ratio: 1/1) {
  .details-row {
    flex-direction: column;
    margin-top: 5rem;
    justify-content: space-around;
    align-items: center;
  }

  .gallery-container,
  .text {
    width: 82%;
    margin: 0 0 3em 0;
  }

  .gallery-container-vertical {
    width: 95%;
    margin: 0 0 3em 0;
  }

  .text {
    height: auto;
    justify-content: flex-start;
    align-items: flex-start;
  }
}

@media only screen and (max-width: 576px) {
  p,
  h6 {
    font-size: 2rem;
  }
}
</style>
