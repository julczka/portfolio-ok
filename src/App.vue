<template>
  <div id="app">
    <!-- :class="{
      dark: darkMode,
      light: !darkMode,
    }" -->

    <div id="nav">
      <div id="homeButton">
        <router-link to="/"><i class="fas fa-home"></i></router-link>
      </div>
      <!-- <div class="mq-test">
        hello
      </div> -->
      <div
        id="themeButton"
        v-on:click="
          darkMode = !darkMode;
          cssTween();
        "
      >
        <transition @enter="enter" @leave="leave" mode="out-in" :css="false">
          <i v-if="darkMode" key="dark" class="fas fa-sun jello-horizontal"></i>
          <i v-else key="light" class="fas fa-moon "></i>
        </transition>
      </div>
    </div>
    <Navigation />
    <div class="view-wrapper">
      <transition @enter="enter" @leave="leave" mode="out-in" :css="false">
        <router-view />
      </transition>
    </div>
    <Background
      ref="background"
      :height="height"
      :key="height"
      :dark="darkMode"
    />
  </div>
</template>

<script>
import gsap from "gsap";

import Navigation from "../src/components/Navigation";
import Background from "../src/components/Background";

export default {
  components: {
    Navigation: Navigation,
    Background: Background
  },
  data() {
    return {
      darkMode: false,
      height: 0,
      darkModeTween: new gsap.timeline({ paused: true })
    };
  },

  watch: {
    $route() {
      console.log("route switched");
      this.$nextTick(() => {
        this.height = this.$el.scrollHeight;
        console.log(this.$el.scrollHeight, this.height);
      });
    }
  },

  methods: {
    cssTween: function() {
      this.darkModeTween.reversed(!this.darkModeTween.reversed());
    },

    enter(el, done) {
      gsap.fromTo(
        el,
        { opacity: 0, scale: 1.5 },
        {
          opacity: 1,
          scale: 1,
          duration: 0.4,
          ease: "power(3)",
          onComplete: done
        }
      );
    },

    leave(el, done) {
      gsap.fromTo(
        el,
        { opacity: 1, scale: 1 },
        {
          opacity: 0,
          scale: 0.5,
          duration: 0.4,
          ease: "power(3)",
          onComplete: done
        }
      );
    }
  },

  mounted() {
    // var rule = CSSRulePlugin.getRule("#app:after");

    this.darkModeTween.to("html", 0.5, {
      "--text-primary": "#df485c",
      ease: "power4.out"
    });

    this.darkModeTween.to("html", 1.4, {
      "--bg-primary": "#202326",
      ease: "power4.out"
    });

    this.darkModeTween.to(
      "html",
      0.5,
      {
        "--gradient-bg-rgba": "rgba(31, 35, 38, 0)",
        ease: "power4.out"
      },
      "<"
    );

    this.darkModeTween.to(
      "html",
      0.5,
      {
        "--gradient-accent-rgba": "rgba(94, 46, 55, 1)",
        ease: "power4.out"
      },
      "<"
    );

    this.darkModeTween.to("html", 0.5, {
      "--bg-secondary": "#823541",
      ease: "power4.out"
    });

    this.darkModeTween.to(
      "html",
      0.5,
      {
        "--text-secondary": "#d9d7d8",
        ease: "power4.out"
      },
      "<"
    );

    this.darkModeTween.reverse();
    window.onresize = () => {
      this.$nextTick(() => {
        this.height = this.$el.scrollHeight;
        console.log(this.$el.scrollHeight, this.height);
      });
    };
    // this.$nextTick(() => {
    //   this.height = this.$el.scrollHeight;
    //   console.log(this.$el.scrollHeight, this.height);
    // });
  }
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
  --text-primary: #202326; // "#df485c" - light pink
  --text-secondary: #595859; // "#d9d7d8" - dark pink
  --bg-primary: #d9d7d8; //"#202326"
  --bg-secondary: #c1c0c1; // "#823541"
  --gradient-bg-rgba: rgba(217, 215, 216, 0);
  --gradient-accent-rgba: rgba(189, 188, 189, 1);
}
*,
*:before,
*:after {
  box-sizing: inherit;
}

:root {
  font-size: 16px;
  font-family: reross-quadratic, sans-serif;

  font-weight: 400;

  font-style: normal;
  letter-spacing: 1px;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  // color: var(--text-primary);
  background-color: var(--bg-primary);
  min-height: 100vh;
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  //width: calc(100vw - 0.25rem);
}

#themeButton {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 1em 1em;
  position: fixed;
  right: 0;
}

#homeButton {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 1em 1em;
  position: fixed;
  left: 0;
}

#nav {
  position: relative;
  z-index: 79;

  .fas:hover {
    -webkit-animation: jello-horizontal 0.9s both;
    animation: jello-horizontal 0.9s both;
  }

  i {
    font-size: 3rem;
  }
}

.view-wrapper {
  position: relative;
  z-index: 69;
  width: 100%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  margin-top: 2em;
  min-height: calc(100vh - 2em);
}

a {
  text-decoration: none;
  color: var(--text-primary);

  &.router-link-exact-active {
    color: $grey-light-hex;
  }
}

i {
  color: var(--text-primary);
}

h1 {
  font-size: 4rem;
  color: var(--text-primary);
  font-weight: normal;
  font-style: normal;
  margin: 0;
}

h2 {
  font-size: 3.5rem;
  color: var(--text-primary);
  font-weight: normal;
  font-style: normal;
  margin: 0;
}
h3 {
  font-size: 3rem;
  color: var(--text-primary);
  font-weight: normal;
  font-style: normal;
  margin: 0;
}
h4 {
  font-size: 2rem;
  color: var(--text-primary);
  font-weight: normal;
  font-style: normal;
  margin: 0;
}
h5 {
  font-size: 1.5rem;
  color: var(--text-primary);
  font-weight: normal;
  font-style: normal;
  margin: 0;
}
h6 {
  font-size: 1rem;
  color: var(--text-primary);
  font-weight: normal;
  font-style: normal;
  margin: 0;
}

button {
  border: 1.5px solid var(--bg-secondary);
  color: var(--text-primary);
  background: var(--bg-primary);
  font-size: 1rem;
  padding: 0.5em;
  min-width: 8em;
  font-family: Arial, Helvetica, sans-serif;
  font-family: futura-pt, sans-serif;
  font-weight: 500;
  margin: 0.5em;
}

@import "./styles/_jello-keyframes.scss";

@media only screen and (max-width: 374px) {
  :root {
    font-size: 8px;
    color: pink;
  }

  #nav {
    i {
      font-size: 5rem;
    }
  }
}

@media only screen and (min-width: 375px) {
  :root {
    font-size: 8px;
    color: pink;
  }

  #nav {
    i {
      font-size: 5rem;
    }
  }
}

@media only screen and (min-width: 576px) {
  :root {
    font-size: 10px;
    color: aqua;
  }

  #nav {
    i {
      font-size: 4rem;
    }
  }
}

@media only screen and (min-width: 768px) {
  :root {
    font-size: 12px;
    color: blue;
  }

  #nav {
    i {
      font-size: 3rem;
    }
  }
}

@media only screen and (min-width: 992px) {
  :root {
    font-size: 14px;
    color: chartreuse;
  }
}

@media only screen and (min-width: 1200px) {
  :root {
    font-size: 16px;
    color: coral;
  }
}

@media only screen and (min-width: 1440px) {
  :root {
    font-size: 18px;
    color: crimson;
  }
}
</style>
