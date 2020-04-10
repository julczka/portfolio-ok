<template>
  <div class="home">
    <router-link to="/Works">
      <div class="link underline">
        <div class="img"></div>
        <div class="name hover hover-3">
          <h2>
            Works
          </h2>
        </div>
      </div>
    </router-link>

    <router-link to="/About">
      <div class="link underline">
        <div class="img img_about"></div>
        <div class="name hover hover-3">
          <h2>
            About
          </h2>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "Home",
  components: {},

  mounted() {
    gsap.fromTo(
      ".img",
      10,
      { scale: 1 },
      {
        scale: 1.1,
        repeat: -1,
        stagger: 0.5,
        repeatDelay: 0,
        ease: "power1.inOut",
        yoyo: true,
        transformOrigin: "center center",
        immediateRender: true,
      }
    );
  },
};
</script>

<style lang="scss" scoped>
@import "../styles/_line-hover.scss";

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
  font-size: 2rem;
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
  width: 7em;
  height: 7em;
  background-image: url("../assets/mirka.png");
  background-size: cover;
  background-position: center;
  transition: $animate;

  &_about {
    background-image: url("../assets/about-ME.jpg");
  }

  &:hover {
    transform: scale(1.1);
  }
}

.name {
  display: flex;
  align-items: center;
  justify-content: center;

  h2 {
    margin: 0.2em;
    color: var(--text-primary);
  }
}

@media screen and (max-width: 375px) {
  .link {
    font-size: 1.8rem;
  }
}

@media screen and (max-width: 576px) {
}

@media screen and (max-width: 768px) and (max-aspect-ratio: 1/1) {
  .home {
    align-self: flex-start;
    flex-direction: column;
    height: calc(100vh - 4em);
    justify-content: flex-start;
  }
}

@media screen and (max-widthh: 992px) {
  .link {
    font-size: 3rem;
  }
}

@media only screen and (max-width: 1200px) {
}
</style>
