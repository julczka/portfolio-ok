<template>
  <div class="nav-wrapper">
    <div class="nav-menu-btn">
      <button type="button" @click="showNav = !showNav">
        <i v-if="showNav" class="fas fa-times"></i>
        <i v-else class="fas fa-bars" />
      </button>
    </div>
    <transition @enter="enter" @leave="leave" :css="false">
      <div class="menu" v-if="showNav">
        <transition-group
          appear
          @enter="listEnter('ul')"
          :css="false"
          tag="ul"
          class="nav-container"
        >
          <ul v-for="link in navLinks" v-bind:key="link.id">
            <li @click="showNav = !showNav" class="underline">
              <router-link :to="link.path" class="hover hover-3">{{
                link.mainLink
              }}</router-link>
            </li>
            <ul
              v-for="subLink in link.subLinks"
              v-bind:key="subLink.id"
              class="minor"
            >
              <li class="underline" @click="showNav = !showNav">
                <router-link class="minor hover hover-3" :to="subLink.path">{{
                  subLink.name
                }}</router-link>
              </li>
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
          id: 1,
          mainLink: "Works",
          path: "/Works",
          subLinks: [
            { id: 11, name: "video", path: "/About#skills" },
            { id: 12, name: "Code", path: "/About#resume" },
            { id: 13, name: "Design", path: "/About#contact" },
          ],
        },
        {
          id: 2,
          mainLink: "About me",
          path: "/About",
          subLinks: [
            { id: 21, name: "skills", path: "/About#skills" },
            { id: 22, name: "resume", path: "/About#resume" },
            { id: 23, name: "contact", path: "/About#contact" },
          ],
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
        { opacity: 0, y: "300px" },
        {
          opacity: 1,
          y: "0px",
          duration: 0.7,
          ease: "power4.out",
          onComplete: done,
        }
      );
    },

    listEnter(el, done) {
      gsap.fromTo(
        el,
        { opacity: 0, x: "200px" },
        {
          opacity: 1,
          x: "0px",
          duration: 0.5,
          ease: "back.inOut(3)",
          onComplete: done,
          stagger: 0.1,
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
        { opacity: 1, y: "0px" },
        {
          opacity: 0,
          y: "400px",
          duration: 0.7,
          ease: "power4.in",
          onComplete: done,
        }
      );
    },
  },
};
</script>

<style lang="scss" scoped>
.nav-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-menu-btn {
  position: fixed;
  margin: 1.2em 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 99;
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
  padding: 0.5em;
  font-size: 3rem;
  color: #202326;
  background: #df485c;
  border-radius: 50%;
  box-sizing: padding-box;
  position: relative;
  z-index: 99;
}

.menu {
  position: fixed;

  z-index: 89;
  top: 0;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #df485c;
  height: 100vh;
  width: 100%;
}

.nav-container {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  flex-direction: column;
  height: 80%;
}

ul {
  list-style: none;
  margin: 0.2em 0;
  padding: 0;
  transform: translateY(-10%);
}

li {
  padding: 0.2em;
  color: #141418;
  text-align: center;
  font-size: 3rem;
}

a {
  color: #141418;
}

.minor {
  font-size: 2.5rem;
  color: #823541;
  text-transform: capitalize;
}

@import "../styles/_line-hover.scss";

@media screen and (min-aspect-ratio: 1/1) and (max-width: 1024px) {
  .nav-container {
    display: flex;
    align-items: flex-end;
    justify-content: space-around;
    flex-direction: row;
    width: 80%;
    height: 100%;
  }
}

@media only screen and (max-width: 375px) {
  i {
    outline: none;
    padding: 0.5em;
    font-size: 5rem;
  }

  li {
    font-size: 3.5rem;
  }

  .minor {
    font-size: 3rem;
  }
}

@media only screen and (min-width: 376px) and (max-width: 576px) {
  i {
    outline: none;
    padding: 0.5em;
    font-size: 4rem;
  }
}

@media only screen and (min-width: 1200px) {
  li {
    font-size: 2rem;
  }

  .minor {
    font-size: 1.5rem;
  }
}

@media only screen and (min-width: 1440px) {
  // li {
  //   font-size: 3rem;
  // }

  // .minor {
  //   font-size: 2.5rem;
  // }
}
</style>
