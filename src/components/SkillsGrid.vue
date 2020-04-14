<template>
  <div class="skill-grid">
    <div class="button-wrapper">
      <h5>Show category:</h5>
      <button
        v-for="(entry, index) in filterList"
        :key="index"
        @click="
          setFilter(entry);
          setIndex(index);
        "
      >
        {{ entry.toUpperCase() }}
      </button>
    </div>

    <transition-group
      @enter="skillEnter(`.${filter}`)"
      @leave="skillLeave"
      :css="false"
      tag="div"
      class="parent"
    >
      <div
        v-for="skill in filteredSkills"
        :key="skill.id"
        :class="[
          `div${filteredSkills.indexOf(skill)}`,
          `${skill.category}`,
          `all`
        ]"
      >
        <Skill :name="skill.name" :icon="skill.icon" :awesome="skill.awesome" />
      </div>
    </transition-group>
  </div>
</template>

<script>
import Skill from "../components/Skill.vue";
import skillsData from "../data/skills.json";
import gsap from "gsap";
export default {
  nane: "SkillsGrid",
  components: {
    Skill: Skill
  },
  data() {
    return {
      skills: skillsData,
      fkey: "category",
      filterList: ["code", "design", "film", "all"],
      filter: "all",
      filterIndex: 0
    };
  },
  computed: {
    filteredSkills: function() {
      var vm = this;
      var category = vm.filter;

      if (category === "all") {
        return vm.skills;
      } else {
        return vm.skills.filter(function(skill) {
          return skill.category === category;
        });
      }
    },
    filtersNegative: function() {
      let filters = [...this.filterList];
      let i = this.filterIndex;
      filters.splice(i, 1);
      return filters.map(item => `.${item}`);
    }
  },
  methods: {
    setFilter: function(entry) {
      this.filter = entry;
      // console.log(entry, this.filter);
    },

    setIndex: function(index) {
      this.filterIndex = index;
      console.log(index, this.filterIndex, this.filtersNegative);
    },

    skillEnter(el, done) {
      let tl = gsap.timeline({ paused: true });

      tl.fromTo(
        el,
        { opacity: 0, scale: 0 },
        {
          opacity: 1,
          scale: 1,
          duration: 1,
          ease: "back.inOut(3)",
          onComplete: done,
          stagger: 0.1
        }
      );
      // tl.to(`.${this.filter}`, { opacity: 1 });
      tl.play();
    },

    skillLeave(el, done) {
      gsap.fromTo(
        el,
        { opacity: 1, scale: 1 },
        {
          opacity: 0,
          scale: 0,
          duration: 1,
          ease: "back.inOut(3)",
          onComplete: done,
          stagger: 0.1
        }
      );
      // gsap.to(`${this.filtersNegative}`, { opacity: 1 });
    }
  }
};
</script>

<style lang="scss" scoped>
h1 {
  color: var(--bg-secondary);
}

h3 {
  font-family: futura-pt, sans-serif;
}

.skill-grid {
  width: 100%;
  @include flex-center();
  flex-direction: column;
  justify-content: space-around;
}

.button-wrapper {
  @include flex-center();
  width: 60%;
  justify-content: space-evenly;
  margin: 2em 1em;
  flex-wrap: wrap;
}
.parent {
  width: 60%;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  // grid-template-columns: repeat(auto-fit, minmax(8rem, 1fr));
  grid-column-gap: 2em;
  grid-row-gap: 2em;
  justify-items: center;
  align-items: end;
  grid-auto-flow: row;
}

.div0 {
  grid-area: 1 / 1 / 2 / 2;
}
.div1 {
  grid-area: 1 / 2 / 2 / 3;
}
.div2 {
  grid-area: 1 / 3 / 2 / 4;
}
.div3 {
  grid-area: 1 / 4 / 2 / 5;
}
.div4 {
  grid-area: 2 / 1 / 3 / 2;
}
.div5 {
  grid-area: 2 / 2 / 3 / 3;
}
.div6 {
  grid-area: 2 / 3 / 3 / 4;
}
.div7 {
  grid-area: 2 / 4 / 3 / 5;
}
.div8 {
  grid-area: 3 / 1 / 4 / 2;
}
.div9 {
  grid-area: 3 / 2 / 4 / 3;
}
.div10 {
  grid-area: 3 / 3 / 4 / 4;
}
.div11 {
  grid-area: 3 / 4 / 4 / 5;
}
.div12 {
  grid-area: 4 / 1 / 5 / 2;
}
.div13 {
  grid-area: 4 / 2 / 5 / 3;
}
.div14 {
  grid-area: 4 / 3 / 5 / 4;
}
.div15 {
  grid-area: 4 / 4 / 5 / 5;
}

@media screen and (max-width: 576px) and (max-aspect-ratio: 1/1) {
  .parent {
    width: 75%;

    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(5, 1fr);
    // grid-template-columns: repeat(auto-fit, minmax(8rem, 1fr));
  }

  .div0 {
    grid-area: 1 / 1 / 2 / 2;
  }
  .div1 {
    grid-area: 1 / 2 / 2 / 3;
  }
  .div2 {
    grid-area: 1 / 3 / 2 / 4;
  }
  .div3 {
    grid-area: 2 / 1 / 3 / 2;
  }
  .div4 {
    grid-area: 2 / 2 / 3 / 3;
  }
  .div5 {
    grid-area: 2 / 3 / 3 / 4;
  }
  .div6 {
    grid-area: 3 / 1 / 4 / 2;
  }
  .div7 {
    grid-area: 3 / 2 / 4 / 3;
  }
  .div8 {
    grid-area: 3 / 3 / 4 / 4;
  }
  .div9 {
    grid-area: 4 / 1 / 5 / 2;
  }
  .div10 {
    grid-area: 4 / 2 / 5 / 3;
  }
  .div11 {
    grid-area: 4 / 3 / 5 / 4;
  }
  .div12 {
    grid-area: 5 / 1 / 6 / 2;
  }
  .div13 {
    grid-area: 5 / 2 / 6 / 3;
  }
  .div14 {
    grid-area: 5 / 3 / 6 / 4;
  }
  .div15 {
    grid-area: 6 / 1 / 7 / 2;
  }
}
</style>
