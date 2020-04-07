<template>
  <div
    id="app"
    :class="{
      dark: darkMode,
      light: !darkMode,
    }"
  >
    <div id="themeButton" v-on:click="darkMode = !darkMode">
      <i v-if="darkMode" class="fas fa-sun fa-2x"></i>
      <i v-else class="fas fa-moon fa-2x"></i>
    </div>

    <div id="nav" class="content">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/Works">Works</router-link>
    </div>
    <Navigation />
    <router-view />
  </div>
</template>

<script>
import Navigation from "../src/components/Navigation";

export default {
  components: {
    Navigation: Navigation,
  },
  data() {
    return {
      darkMode: true,
    };
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
  --text-primary: #b6b6b6;
  --text-secondary: #ececec;
  --bg-primary: #23232e;
  --bg-secondary: #141418;
  --transition-speed: 600ms;
  --background-image: url("../src/assets/background.svg");
}

// body::-webkit-scrollbar {
//   width: 0.25rem;
// }

// body::-webkit-scrollbar-track {
//   background: #823541;
// }

// body::-webkit-scrollbar-thumb {
//   background: #df485c;
// }

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--text-primary);
  background-image: var(--background-image);
  background-position: top center;
  background-repeat: no-repeat;
  background-size: 100vw;
  background-color: var(--bg-primary);
  min-height: 100vh;
  //width: calc(100vw - 0.25rem);
}

#themeButton {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 1em;
  position: fixed;
  right: 0;
}

#nav {
  padding: 30px;
  z-index: 1;
}

a {
  color: #2c3e50;
  text-decoration: none;

  &.router-link-exact-active {
    color: var(--text-secondary);
  }
}

.dark {
  --text-primary: #df485c;
  --text-secondary: #d9d7d8;
  --bg-primary: #202326;
  --bg-secondary: #823541;
  --background-image: url("../src/assets/background-dark.svg");
}

.light {
  --text-primary: #202326;
  --text-secondary: #595859;
  --bg-primary: #d9d7d8;
  --bg-secondary: #c1c0c1;
  --background-image: url("../src/assets/background.svg");
}
</style>
