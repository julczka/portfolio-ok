<template>
  <div class="wrapper">
    <div class="menu-btn" @click="showNav = !showNav">
      <button type="button">
        <i v-if="showNav" class="fas fa-times fa-3x"></i>
        <i v-else class="fas fa-bars fa-3x" />
      </button>
    </div>

    <div class="menu" v-if="showNav">
      <ul>
        <router-link to="/Works"
          ><li @click="showNav = !showNav">Works</li></router-link
        >
        <li class="minor">Video</li>
        <li class="minor">Code</li>
        <li class="minor">Design</li>
        <router-link to="/about"
          ><li @click="showNav = !showNav">About me</li></router-link
        >
        <li class="minor">Skills</li>
        <li class="minor">Resume</li>
        <li class="minor">Contact</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navigation",
  data() {
    return {
      showNav: false,
    };
  },
};
</script>

<style lang="scss" scoped>
.menu-btn {
  position: fixed;
  margin: 1.2rem;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
}

button {
  border: none;
  background: none;
}

button:focus {
  outline: none !important;
}

i {
  outline: none;
  padding: 1.5rem;
  color: #202326;
  background: #df485c;
  border-radius: 50%;
  box-sizing: padding-box;
}

.menu {
  position: fixed;
  top: 0;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #df485c;
  height: 100vh;
  width: 100%;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  transform: translateY(-10%);
}

li {
  padding: 0.2em;
  color: #141418;
  text-align: center;
  font-size: 3rem;
}

.minor {
  font-size: 2rem;
  color: #823541;
}
</style>
