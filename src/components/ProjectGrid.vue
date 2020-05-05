<template>
  <div class="parent">
    <div
      v-for="project in projects"
      :key="project.id"
      :class="[`div${project.id}`, 'bcg']"
    >
      <div
        class="img"
        :style="{
          'background-image': 'url(' + require(`../assets/${imgPath}`) + ')',
        }"
      ></div>
      <div class="txt">
        <h5>
          {{ project.projectTitle }}
        </h5>
        <h6>{{ project.category }}</h6>
      </div>
    </div>
    <!-- <div class="div2 bcg">
      <div
        class="img"
        :style="{
          'background-image': 'url(' + require(`../assets/${imgPath}`) + ')',
        }"
      ></div>
      <div class="txt">
        <h4>
          Project 2
        </h4>
        <h5>Omnis super addvert</h5>
      </div>
    </div>
    <div class="div3 bcg">
      <div class="img"></div>
      <div class="txt">
        <h4>
          Project 3
        </h4>
        <h5>Omnis super addvert</h5>
      </div>
    </div>
    <div class="div4 bcg">
      <div class="img"></div>
      <div class="txt">
        <h4>
          Project 4
        </h4>
        <h5>Omnis super addvert</h5>
      </div>
    </div>
    <div class="div5 bcg">
      <div class="img"></div>
      <div class="txt">
        <h4>
          Project 5
        </h4>
        <h5>Omnis super addvert</h5>
      </div>
    </div>
    <div class="div6 bcg">
      <div class="img"></div>
      <div class="txt">
        <h4>
          Project 6
        </h4>
        <h5>Omnis super addvert</h5>
      </div>
    </div> -->
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
}

.txt {
  width: 13rem;
  height: 13rem;
  @include flex-center();
  flex-direction: column;
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
</style>
