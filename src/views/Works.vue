<template>
  <div class="work">
    <div class="opening-row ">
      <div class="link underline" @click="smoothScroll('#video', 0.6)">
        <div class="img" ref="hover1"></div>
        <div class="name hover hover-3">
          Video
        </div>
      </div>

      <div class="link underline" @click="smoothScroll('#code', 1)">
        <div class="img " ref="hover2"></div>
        <div class="name hover hover-3">
          Code
        </div>
      </div>

      <div class="link underline" @click="smoothScroll('#design', 1.4)">
        <div class="img " ref="hover3"></div>
        <div class="name hover hover-3">
          Design
        </div>
      </div>
    </div>

    <div class="sticky-control">
      <div class="sticky-indicator">
        <div class="page-position" @click="smoothScroll('#video', 1)">
          video
          <div class="line" id="line-video"></div>
        </div>
        <div class="page-position" @click="smoothScroll('#code', 1)">
          code
          <div class="line" id="line-code"></div>
        </div>
        <div class="page-position" @click="smoothScroll('#design', 1)">
          design
          <div class="line" id="line-design"></div>
        </div>
      </div>

      <intersect
        @enter="lineWidth('#line-video', '40%')"
        @leave="lineWidth('#line-video', '0%')"
      >
        <div class="work-row">
          <ProjectGrid :projects="videoProjects" id="video" />
          <h2 class="side-header">Video</h2>
        </div>
      </intersect>

      <intersect
        @enter="lineWidth('#line-code', '40%')"
        @leave="lineWidth('#line-code', '0%')"
      >
        <div class="work-row">
          <ProjectGrid :projects="codeProjects" id="code" />
          <h2 class="side-header">Code</h2>
        </div>
      </intersect>

      <intersect
        @enter="lineWidth('#line-design', '40%')"
        @leave="lineWidth('#line-design', '0%')"
      >
        <div class="work-row">
          <ProjectGrid :projects="designProjects" id="design" />
          <h2 class="side-header">Design</h2>
        </div>
      </intersect>
    </div>
  </div>
</template>

<script>
import ProjectGrid from '../components/ProjectGrid';
import ProjectsVideo from '../data/projects-video.json';
import ProjectsCode from '../data/projects-code.json';
import ProjectsDesign from '../data/projects-design.json';
import Intersect from 'vue-intersect';

import { gsap } from 'gsap';
import { ScrollToPlugin } from 'gsap/ScrollToPlugin';

gsap.registerPlugin(ScrollToPlugin);

import hoverEffect from 'hover-effect';

export default {
  components: {
    ProjectGrid,
    Intersect,
  },
  data() {
    return {
      videoProjects: ProjectsVideo,
      codeProjects: ProjectsCode,
      designProjects: ProjectsDesign,
    };
  },

  methods: {
    smoothScroll(el, duration) {
      gsap.to(window, {
        duration: duration,
        scrollTo: { y: el, offsetY: 55 },
        ease: 'power2',
      });
    },

    lineWidth(el, val) {
      gsap.to(el, {
        duration: 0.3,
        width: val,
        ease: 'power2',
      });
    },
  },

  mounted() {
    new hoverEffect({
      parent: this.$refs.hover1,
      intensity1: 0.1,
      intensity2: 0.1,
      angle2: Math.PI / 2,
      image1: require('../assets/hovers/hover-img-video/elektro3-1 copy.jpg'),
      image2: require('../assets/hovers/hover-img-video/wyscig30.jpg'),
      displacementImage: require('../assets/bump22.png'),
      easing: 'slow',
    });

    new hoverEffect({
      parent: this.$refs.hover2,
      intensity1: 0.1,
      intensity2: 0.1,
      angle2: Math.PI / 2,
      image1: require('../assets/hovers/hover-img-video/planxlap3d-hov.jpg'),
      image2: require('../assets/hovers/hover-img-video/planxl-hov2.jpg'),
      displacementImage: require('../assets/bump22.png'),
      easing: 'slow',
    });

    new hoverEffect({
      parent: this.$refs.hover3,
      intensity1: 0.1,
      intensity2: 0.1,
      angle2: Math.PI / 2,
      image1: require('../assets/hovers/hover-img-video/krise3-hov.png'),
      image2: require('../assets/hovers/hover-img-video/outsbjerg_mock.jpg'),
      displacementImage: require('../assets/bump22.png'),
      easing: 'slow',
    });
  },
};
</script>

<style lang="scss" scoped>
.work {
  width: 100%;

  // @include flex-center();
  // flex-direction: column;

  h2 {
    color: var(--bg-secondary);
    font-size: 7rem;
    margin: 0 0.5em;
    writing-mode: vertical-rl;
  }
}

.opening-row {
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: calc(100vh - 2em);
  width: 100%;
}

.link {
  display: flex;
  align-items: center;
  justify-content: center;

  flex-direction: column;
  font-size: 3rem;
  margin: 0.5em 0;
}

.link:nth-child(2) {
  flex-direction: column-reverse;
}

.img {
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 200px;
  filter: grayscale(1);
  width: 6.5em;
  height: 6.5em;
  transition: $animate;

  &:hover {
    filter: grayscale(0.2);
  }

  &:hover + .name {
    transform: scale(1.1);
  }
}

.name {
  display: flex;
  align-items: center;
  justify-content: center;
  transition: $animate;
  margin: 0.5em 0;
  color: var(--text-primary);
}

.sticky-control {
  position: relative;
}

.sticky-indicator {
  position: sticky;
  top: 10rem;
  left: 2rem;
  width: 10%;
}

.page-position {
  padding: 4em 0em 4em 1em;
  display: flex;
  flex-direction: column;
  justify-content: center;
  border-left: 1px solid var(--text-secondary);
  position: relative;
  transition: all 200ms ease-in;
  text-align: left;
  font-family: futura-pt, sans-serif;
  font-weight: 800;
  text-transform: uppercase;
  color: var(--text-secondary);
  cursor: pointer;

  &::before {
    content: '';
    width: 1rem;
    height: 1rem;
    background-color: var(--bg-primary);
    border-radius: 25px;
    border: 1px solid var(--text-primary);
    position: absolute;
    top: 44.9%;
    left: -0.5em;
  }
}

.line {
  position: absolute;
  top: 60.9%;
  left: 1em;
  // width: 50%;
  height: 0.21em;
  background-color: $pink-light-hex;
}
.work-row {
  width: 100%;
  @include flex-center();
  margin-bottom: 9rem;
  justify-content: flex-end; // margin: 1rem 3rem 5rem 3rem;
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

@media only screen and (max-width: 1200px) {
  .side-header {
    display: none;
  }
}

@media screen and (max-aspect-ratio: 1/1) {
  .work-row {
    justify-content: center;
  }

  .opening-row {
    flex-direction: column;
  }

  .link:nth-child(2) {
    flex-direction: column;
  }
}
</style>
