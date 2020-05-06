<template>
  <div class="work">
    <div class="fill">
      here something will go
    </div>
    <div class="sticky-control">
      <div class="sticky-indicator">
        <div class="page-position" @click="smoothScroll('#video')">
          video
          <div class="line" id="line-video"></div>
        </div>
        <div class="page-position" @click="smoothScroll('#code')">
          code
          <div class="line" id="line-code"></div>
        </div>
        <div class="page-position" @click="smoothScroll('#design')">
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
      msg: 'I will change',
      msg2: 'I will change',
      msg3: 'I will change',
    };
  },

  methods: {
    smoothScroll(el) {
      gsap.to(window, {
        duration: 1,
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
};
</script>

<style lang="scss" scoped>
.fill {
  height: 100vh;
}
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

.sticky-control {
  position: relative;
}

.sticky-indicator {
  position: fixed;
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
}
</style>
