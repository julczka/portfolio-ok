<template>
  <div class="wrapper">
    <div class="menu-btn" @click="showNav = !showNav">
      <button type="button">
        <i v-if="showNav" class="fas fa-times fa-3x"></i>
        <i v-else class="fas fa-bars fa-3x" />
      </button>
    </div>
    <transition @enter="enter" @leave="leave" :css="false">
      <div class="menu" v-if="showNav">
        <transition-group appear @enter="listEnter('ul')" :css="false" tag="ul">
          <ul v-for="(link, index) in navLinks" v-bind:key="index">
            <li>
              <router-link :to="link.path">{{ link.mainLink }}</router-link>
            </li>
            <ul v-for="(subLink, indeks) in link.subLinks" v-bind:key="indeks">
              <li class="minor">{{ subLink }}</li>
            </ul>
          </ul>
          <!-- <li @click="showNav = !showNav">
              <router-link to="/Works">Works</router-link>
            </li>
            <li class="minor">Video</li>
            <li class="minor">Code</li>
            <li class="minor">Design</li>
            <li @click="showNav = !showNav">
              <router-link to="/about">About me</router-link>
            </li>
            <li class="minor">Skills</li>
            <li class="minor">Resume</li>
            <li class="minor">Contact</li> -->
        </transition-group>
      </div>
    </transition>
  </div>
</template>

<script>
import gsap from "gsap";
export default {
  name: "Navigation",
  data() {
    return {
      showNav: false,
      navLinks: [
        {
          mainLink: "Works",
          path: "/Works",
          subLinks: ["Video", "Design", "code"],
        },
        {
          mainLink: "About me",
          path: "/About",
          subLinks: {
            link1: "skills",
            link2: "resume",
            link3: "contact",
          },
        },
      ],

      // "Works",

      // "about me",
      // "skills",
      // "resume",
      // "contact",
    };
  },
  methods: {
    enter(el, done) {
      gsap.fromTo(
        el,
        { opacity: 0, scale: 0 },
        {
          opacity: 1,
          scale: 1,
          duration: 0.7,
          ease: "back.inOut(3)",
          onComplete: done,
        }
      );
    },

    listEnter(el, done) {
      gsap.fromTo(
        el,
        { opacity: 0, x: 400 },
        {
          opacity: 1,
          x: 1,
          duration: 1,
          ease: "back.inOut(3)",
          onComplete: done,
          stagger: 0.2,
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
          duration: 0.7,
          ease: "back.inOut(3)",
          onComplete: done,
        }
      );
    },
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

  a {
    color: #141418;
  }
}

.minor {
  font-size: 2rem;
  color: #823541;
  text-transform: capitalize;
}
</style>
