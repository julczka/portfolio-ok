<template>
  <div class="parent">
    <div
      v-for="(project, index) in projects"
      :key="project.id"
      :class="[`div${index + 1}`, 'bcg']"
    >
      <router-link
        v-if="project.projectTitle"
        :to="{ name: 'ProjectDetails', params: { ...project } }"
        :class="[`div${index + 1}`, 'bcg']"
      >
        <div
          v-if="project.imgCover"
          class="img"
          :style="{
            'background-image':
              'url(' + require(`../assets/${project.imgCover}`) + ')',
          }"
        ></div>
        <div v-else class="img"></div>
        <div class="txt">
          <h5>
            {{ project.projectTitle }}
          </h5>
          <h6>{{ project.category }}</h6>
        </div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    projects: Array,
  },
  data() {
    return {
      imgStatic: '/cover_img/mirka.png',
      imgPath: 'mirka.png',
    };
  },

  methods: {},
};
</script>

<style lang="scss" scoped>
.parent {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-column-gap: 10px;
  grid-row-gap: 10px;
  margin-right: 3em;
}

.bcg {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 200px;
}

.img {
  //   background-image: url("../assets/mirka.png");
  background-size: cover;
  background-position: center;
  width: 13rem;
  height: 13rem;
  border-radius: 200px;
  filter: grayscale(1);
  transition: $animate;

  &:hover {
    filter: grayscale(0.2);
    // transform: scale(1.05);
  }

  &:hover + .txt {
    opacity: 1;
    transform: scale(1.05);
  }
}

.txt {
  width: 13rem;
  height: 13rem;
  @include flex-center();
  flex-direction: column;
  transition: $animate;
  opacity: 0.3;
  &:hover {
    opacity: 1;
  }
}

.div1 {
  grid-area: 2 / 1 / 3 / 3;
  @include gird-gradient(90deg);
}
.div2 {
  flex-direction: column-reverse;
  @include gird-gradient(0deg);

  grid-area: 1 / 3 / 3 / 4;
}
.div3 {
  flex-direction: row-reverse;
  grid-area: 3 / 3 / 4 / 5;
  @include gird-gradient(270deg);
}
.div4 {
  flex-direction: row-reverse;
  grid-area: 1 / 1 / 2 / 3;
  @include gird-gradient(270deg);
}
.div5 {
  flex-direction: row-reverse;
  grid-area: 3 / 1 / 4 / 3;
  @include gird-gradient(270deg);
}
.div6 {
  flex-direction: column;
  @include gird-gradient(180deg);
  grid-area: 1 / 4 / 3 / 5;
}

@media screen and (max-aspect-ratio: 1/1) {
  .parent {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(6, 1fr);
    margin-right: 0em;
  }

  .div1 {
    flex-direction: row-reverse;
    @include gird-gradient(-90deg);
    grid-area: 2 / 1 / 3 / 3;
  }
  .div2 {
    flex-direction: column;
    @include gird-gradient(180deg);
    grid-area: 3 / 1 / 5 / 2;
  }
  .div3 {
    flex-direction: column-reverse;
    @include gird-gradient(0deg);
    grid-area: 3 / 2 / 5 / 3;
  }
  .div4 {
    flex-direction: row;
    @include gird-gradient(90deg);
    grid-area: 5 / 1 / 6 / 3;
  }
  .div5 {
    flex-direction: row;
    @include gird-gradient(90deg);
    grid-area: 1 / 1 / 2 / 3;
  }
  .div6 {
    flex-direction: row-reverse;
    @include gird-gradient(-90deg);
    grid-area: 6 / 1 / 7 / 3;
  }
}
</style>
