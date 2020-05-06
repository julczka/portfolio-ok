<template>
  <div>
    <h5>
      {{ currentProject.projectTitle }}
    </h5>
    <h6>{{ currentProject.category }}</h6>
    <h6>{{ currentProject.description }}</h6>
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

<style lang="scss" scoped></style>
