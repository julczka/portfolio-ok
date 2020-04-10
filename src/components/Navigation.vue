<template>
  <div class="wrapper">
    <div class="menu-btn" @click="showNav = !showNav">
      <button type="button">
        <i v-if="showNav" class="fas fa-times fa-3x"></i>
        <i v-else class="fas fa-bars fa-3x" />
      </button>
    </div>
    <transition @enter="enter" @leave="leave" :css="false">
      <div id="examples" class="menu" v-if="showNav">
        <transition-group appear @enter="listEnter('ul')" :css="false" tag="ul">
          <ul v-for="(link, index) in navLinks" v-bind:key="index">
            <li @click="showNav = !showNav" class="example">
              <router-link :to="link.path" class="hover hover-3">{{
                link.mainLink
              }}</router-link>
            </li>
            <ul v-for="subLink in link.subLinks" v-bind:key="subLink">
              <li class="minor example" @click="showNav = !showNav">
                <router-link class="minor hover hover-3" to="/">{{
                  subLink
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
        { opacity: 0, y: 300 },
        {
          opacity: 1,
          y: 0,
          duration: 0.7,
          ease: "power4.out",
          onComplete: done,
        }
      );
    },

    listEnter(el, done) {
      gsap.fromTo(
        el,
        { opacity: 0, x: 200 },
        {
          opacity: 1,
          x: 1,
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
        { opacity: 1, y: 0 },
        {
          opacity: 0,
          y: 400,
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
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.menu-btn {
  position: fixed;
  margin: 1.2rem;
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
  padding: 1.5rem;
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
  font-size: 2.7rem;
}

a {
  color: #141418;
}

.minor {
  font-size: 1.7rem;
  color: #823541;
  text-transform: capitalize;
}

$animate: all 0.2s ease-in-out;

#examples {
  .example {
    .hover {
      transition: $animate;
      position: relative;
      &:before,
      &:after {
        content: "";
        position: absolute;
        bottom: -2px;
        width: 0px;
        height: 0.12em;
        margin: 5px 0 0;
        transition: $animate;
        transition-duration: 0.3s;
        opacity: 0;
        background-color: lighten(#823541, 30%);
      }
      &.hover-1 {
        &:before,
        &:after {
          left: 0;
        }
      }
      &.hover-2 {
        &:before,
        &:after {
          right: 0;
        }
      }
      &.hover-3 {
        &:before {
          left: 50%;
        }
        &:after {
          right: 50%;
        }
      }
      &.hover-4 {
        &:before {
          left: 0;
        }
        &:after {
          right: 0;
        }
      }
    }
    &:hover {
      cursor: pointer;
      .hover {
        &:before,
        &:after {
          width: 100%;
          opacity: 1;
        }
        &.hover-3,
        &.hover-4 {
          &:before,
          &:after {
            width: 50%;
          }
        }
      }
    }
  }
}
</style>
