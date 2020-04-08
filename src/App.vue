<template>
  <div id="app">
    <!-- :class="{
      dark: darkMode,
      light: !darkMode,
    }" -->
    <div id="nav">
      <div id="homeButton">
        <router-link to="/"><i class="fas fa-home fa-2x"></i></router-link>
      </div>

      <div
        id="themeButton"
        v-on:click="
          darkMode = !darkMode;
          cssTween();
        "
      >
        <transition @before-enter="beforeEnter" @enter="enter" :css="false">
          <i v-if="darkMode" key="dark" class="fas fa-sun fa-2x"></i>
          <i v-else key="light" class="fas fa-moon fa-2x"></i>
        </transition>
      </div>
    </div>
    <Navigation />

    <router-view />
  </div>
</template>

<script>
import gsap from "gsap";
import { CSSRulePlugin } from "gsap/all";
gsap.registerPlugin(CSSRulePlugin);
import Navigation from "../src/components/Navigation";

export default {
  components: {
    Navigation: Navigation,
  },
  data() {
    return {
      darkMode: false,
      darkModeTween: new gsap.timeline({ paused: true }),
    };
  },
  methods: {
    cssTween() {
      this.darkModeTween.reversed(!this.darkModeTween.reversed());
    },

    // beforeEnter(el) {
    //   el.style.opacity = 0;
    //   el.style.transform = "scale(0,0)";
    // },

    enter(el, done) {
      gsap.fromTo(
        el,
        { opacity: 0, scale: 0 },
        {
          opacity: 1,
          scale: 1,
          duration: 0.2,
          ease: "back.inOut(3)",
          onComplete: done,
        }
      );
    },

    // beforeLeave(el) {
    //   el.style.opacity = 1;
    //   el.style.transform = "scale(1,1)";
    // },

    leave(el, done) {
      gsap.fromTo(
        el,
        { opacity: 1, scale: 1 },
        {
          opacity: 0,
          scale: 0,
          duration: 0.2,
          ease: "back.inOut(3)",
          onComplete: done,
        }
      );
    },
  },

  mounted() {
    var rule = CSSRulePlugin.getRule("#app:after");
    this.darkModeTween.to("html", 1.4, { "--bg-primary": "#202326" });
    this.darkModeTween.to(rule, 0.7, { opacity: 0 }, "<");
    this.darkModeTween.set(rule, {
      "background-image": "var(--background-image-dark)",
    });
    this.darkModeTween.to(rule, 0.7, { opacity: 1 });

    this.darkModeTween.to("html", 0.5, { "--bg-secondary": "#823541" }, "<");
    this.darkModeTween.to("html", 0.5, { "--text-primary": "#df485c" });
    this.darkModeTween.to("html", 0.5, { "--text-secondary": "#d9d7d8" });
    this.darkModeTween.reverse();
  },
};
</script>

<style lang="scss">
html,
body {
  margin: 0px !important;
  padding: 0px !important;
}

html {
  box-sizing: border-box;
  --text-primary: #202326;
  --text-secondary: #595859;
  --bg-primary: #d9d7d8;
  --bg-secondary: #c1c0c1;
  --background-image: url("../src/assets/background.svg");
  --background-image-dark: url("../src/assets/background-dark.svg");
}
*,
*:before,
*:after {
  box-sizing: inherit;
}

:root {
  font-size: 16px;
  font-family: reross-quadratic, sans-serif;
  letter-spacing: 1px;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--text-primary);

  min-height: 100vh;
  //width: calc(100vw - 0.25rem);
}

#app:after {
  content: "";
  opacity: 1;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
  background-image: var(--background-image);
  background-position: top center;
  background-repeat: no-repeat;
  background-size: 100vw;
  background-color: var(--bg-primary);
}

#themeButton {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 0 1em;
  position: fixed;
  right: 0;
}

#homeButton {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 0 1em;
  position: fixed;
  left: 0;
}

#nav {
  padding: 1em;
}

a {
  text-decoration: none;
  color: var(--text-primary);

  &.router-link-exact-active {
    color: var(--text-primary);
  }
}

h1 {
  color: var(--bg-secondary);
}

// .dark {
//   // --text-primary: #df485c;
//   // --text-secondary: #d9d7d8;
//   // --bg-primary: #202326;
//   // --bg-secondary: #823541;
//   --background-image: url("../src/assets/background-dark.svg");
// }

// .light {
//   // --text-primary: #202326;
//   // --text-secondary: #595859;
//   // --bg-primary: #d9d7d8;
//   // --bg-secondary: #c1c0c1;
//   --background-image: url("../src/assets/background.svg");
// }
</style>
