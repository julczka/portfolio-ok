<template>
  <div class="work">
    <div class="fill"></div>
    <div class="work-row">
      <ProjectGrid :projects="videoProjects" />
      <h2>Video</h2>
    </div>
    <div class="fill"></div>
  </div>
</template>

<script>
import ProjectGrid from '../components/ProjectGrid';
import ProjectsVideo from '../data/projects-video.json';

export default {
  components: {
    ProjectGrid,
  },
  data() {
    return {
      videoProjects: ProjectsVideo,
    };
  },
};
</script>

<style lang="scss" scoped>
.fill {
  height: 800px;
}
.work {
  width: 100%;

  @include flex-center();
  flex-direction: column;

  h2 {
    color: var(--bg-secondary);
    font-size: 7rem;
    margin: 0 0.5em;
    writing-mode: vertical-rl;
  }
}

.work-row {
  width: 100%;
  @include flex-center();
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
</style>
