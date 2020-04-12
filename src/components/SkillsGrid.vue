<template>
  <div class="skill-grid">
    <h1>What I can do for you</h1>
    <div class="parent">
      <div v-for="skill in skills" :key="skill.id" :class="[`div${skill.id}`]">
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
      skills: skillsData
    };
  }
};
</script>

<style lang="scss" scoped>
h1 {
  color: var(--bg-secondary);
}

.skill-grid {
  width: 90%;
  @include flex-center();
  flex-direction: column;
}

.parent {
  width: 60%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(8rem, 1fr));
  grid-column-gap: 1em;
  grid-row-gap: 1em;
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
