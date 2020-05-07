<template>
  <div class="project_details">
    <div class="gallery-container">
      <div class="image">
        <iframe
          :src="currentProject.videoSrc"
          frameborder="0"
          allow="autoplay; fullscreen"
          allowfullscreen
          width="100%"
          height="100%"
          style="position:absolute; top:0; left: 0"
        ></iframe>
      </div>
    </div>
    <div class="text left ">
      <h1>
        {{ currentProject.projectTitle }}
      </h1>
      <h4>{{ currentProject.category }}</h4>
      <p>{{ currentProject.description }}</p>

      <h6>{{ currentProject.myRole }}</h6>

      <router-link to="/Works">
        <button class="button">Back to works</button>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projectId: this.$route.params.id,
      currentProject: this.$route.params,
    };
  },
};
</script>

<style lang="scss" scoped>
.project_details {
  height: 100vh;
  display: flex;
  justify-content: space-around;
  align-items: center;
  // margin-top: 5em;
}

.gallery-container {
  width: 50%;
  margin: 0 2em 0 5em;
}

.image {
  overflow: hidden;
  width: 100%;
  padding-top: 56.25%;
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

  a {
    align-self: flex-end;
  }
}

p {
  font-family: futura-pt, sans-serif;
  color: var(--text-secondary);
}

.left {
  text-align: left;
}

@media screen and (max-aspect-ratio: 1/1) {
  .project_details {
    flex-direction: column;
    margin-top: 5rem;
    justify-content: space-around;
    align-items: center;
    height: 100%;
  }

  .gallery-container,
  .text {
    width: 82%;
    margin: 0 0 3em 0;
  }

  .text {
    height: auto;
    justify-content: flex-start;
    align-items: flex-start;
  }
}
</style>
