<template>
  <div class="skill-grid">
    <div class="button-wrapper">
      <h6>Show category:</h6>
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
    }
    // filtersNegative: function() {
    //   const filters = this.filterList;
    //   let i = this.filterIndex;
    //   let filtersNegative = filters.splice(i, 1);

    //   return filtersNegative.map(item => `.${item}`);
    // }
  },
  methods: {
    setFilter: function(entry) {
      this.filter = entry;
      console.log(entry, this.filter);
    },

    setIndex: function(index) {
      this.filterIndex = index;
      console.log(index, this.filterIndex, this.filtersNegative);
    },

    skillEnter(el, done) {
      gsap.fromTo(
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
    }
  }
};
</script>

<style lang="scss" scoped>
h1 {
  color: var(--bg-secondary);
}

button {
  border: 1.5px solid var(--bg-secondary);
  color: var(--text-primary);
  background: var(--bg-primary);
  font-size: 1rem;
  padding: 0.5em;
  min-width: 6em;
  font-family: Arial, Helvetica, sans-serif;
  font-family: futura-pt, sans-serif;

  font-weight: 500;

  font-style: normal;
  font-size: 1rem;
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
  justify-content: space-around;
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
</style>
