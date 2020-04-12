<template>
  <div class="skill-grid">
    <div class="button-wrapper">
      <h6>Show category:</h6>
      <button
        v-for="(entry, index) in filterList"
        :key="index"
        @click="setFilter(entry)"
      >
        {{ entry.toUpperCase() }}
      </button>
    </div>
    <div class="parent">
      <div
        v-for="skill in filteredSkills"
        :key="skill.id"
        :class="[`div${skill.id}`]"
      >
        <Skill :name="skill.name" :icon="skill.icon" :awesome="skill.awesome" />
      </div>
    </div>
  </div>
</template>

<script>
import Skill from "../components/Skill.vue";
import skillsData from "../data/skills.json";

export default {
  nane: "SkillsGrid",
  components: {
    Skill: Skill
  },
  data() {
    return {
      skills: skillsData,
      fkey: "category",
      filterList: ["code", "design", "film", "All"],
      filter: "All"
    };
  },
  computed: {
    filteredSkills: function() {
      var vm = this;
      var category = vm.filter;

      if (category === "All") {
        return vm.skills;
      } else {
        return vm.skills.filter(function(skill) {
          return skill.category === category;
        });
      }
    }
  },
  methods: {
    setFilter: function(entry) {
      this.filter = entry;
      console.log(entry, this.filter);
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
}
.parent {
  width: 60%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(8rem, 1fr));
  grid-column-gap: 2em;
  grid-row-gap: 2em;
  justify-items: center;
  align-items: end;
  grid-auto-flow: row;
}

// .div1 {
//   grid-area: 1 / 1 / 2 / 2;
// }
// .div2 {
//   grid-area: 1 / 2 / 2 / 3;
// }
// .div3 {
//   grid-area: 1 / 3 / 2 / 4;
// }
// .div4 {
//   grid-area: 1 / 4 / 2 / 5;
// }
// .div5 {
//   grid-area: 2 / 1 / 3 / 2;
// }
// .div6 {
//   grid-area: 2 / 2 / 3 / 3;
// }
// .div7 {
//   grid-area: 2 / 3 / 3 / 4;
// }
// .div8 {
//   grid-area: 2 / 4 / 3 / 5;
// }
// .div9 {
//   grid-area: 3 / 1 / 4 / 2;
// }
// .div10 {
//   grid-area: 3 / 2 / 4 / 3;
// }
// .div11 {
//   grid-area: 3 / 3 / 4 / 4;
// }
// .div12 {
//   grid-area: 3 / 4 / 4 / 5;
// }
</style>
