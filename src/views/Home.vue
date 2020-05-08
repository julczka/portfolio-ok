<template>
  <div class="home">
    <router-link to="/Works">
      <div class="link underline">
        <div class="img" ref="hoverWorks"></div>
        <div class="name hover hover-3">
          Works
        </div>
      </div>
    </router-link>

    <router-link to="/About">
      <div class="link underline">
        <div class="img img_about" ref="hoverAbout"></div>
        <div class="name hover hover-3">
          About me
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
import hoverEffect from 'hover-effect';
export default {
  name: 'Home',
  components: {},
  mounted() {
    new hoverEffect({
      parent: this.$refs.hoverAbout,
      intensity1: 0.1,
      intensity2: 0.1,
      angle2: Math.PI / 2,
      image1: require('../assets/hovers/hover-img-video/about-hover2-min.jpg'),
      image2: require('../assets/hovers/hover-img-video/about-hover1-min.jpg'),
      displacementImage: require('../assets/bump22.png'),
      easing: 'slow',
    });

    new hoverEffect({
      parent: this.$refs.hoverWorks,
      intensity1: 0.1,
      intensity2: 0.1,
      angle2: Math.PI / 2,
      image1: require('../assets/hovers/hover-img-video/planxl-hov2.jpg'),
      image2: require('../assets/hovers/hover-img-video/elektro3-1 copy.jpg'),
      displacementImage: require('../assets/bump22.png'),
      easing: 'slow',
    });
  },
};
</script>

<style lang="scss" scoped>
@import '../styles/_line-hover.scss';

.home {
  display: flex;
  align-items: center;
  justify-content: space-around;

  width: 80%;
  align-self: center;
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
}

.name {
  display: flex;
  align-items: center;
  justify-content: center;

  margin: 0.5em 0;
  color: var(--text-primary);
}

// @media screen and (max-width: 375px) {
//   .link {
//     font-size: 1.8rem;
//   }
// }

@media screen and (max-aspect-ratio: 1/1) {
  .home {
    align-self: flex-start;
    flex-direction: column;
    height: calc(100vh - 4em);
    justify-content: flex-start;
  }
}

@media screen and (min-width: 992px) {
  .link {
    font-size: 3rem;
  }
}

@media only screen and (min-width: 1200px) {
}
</style>
