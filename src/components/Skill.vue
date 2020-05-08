<template>
  <div class="skill">
    <div class="skill__wrapper">
      <div class="skill__ico">
        <i v-if="awesome" :class="[icon, 'fa-2x']"></i>
        <div v-else><SimpleIcon :iconName="icon" /></div>
      </div>
      <div class="skill__name">{{ name }}</div>
    </div>
  </div>
</template>

<script>
import SimpleIcon from '../components/icons/SimpleIcon';
export default {
  name: 'Skill',
  props: {
    name: {
      type: String,
    },
    icon: {
      type: String,
    },
    awesome: {
      type: Boolean,
    },
  },

  components: {
    SimpleIcon,
  },
};
</script>

<style lang="scss" scoped>
.skill {
  //   border: 4px solid red;
  border-radius: 200px;
  width: 8rem;
  background: $simplegradient;
  box-sizing: content-box;
  margin: 1em;
  transition: $animate;

  &:hover {
    transform: scale(1.1);
  }

  &__ico {
    color: var(--text-primary);
    // border: 4px solid blue;
    font-size: 3rem;
  }

  &__wrapper {
    // border: 4px solid pink;
    @include flex-center;
    flex-direction: column;
    justify-content: space-between;
    position: relative;
    z-index: 4;
  }

  &__name {
    @include flex-center;
    font-family: futura-pt, sans-serif;

    font-weight: 200;

    font-style: normal;
    font-size: 1.5rem;
    padding-bottom: 0.6em;
    width: 130%;
    color: var(--text-secondary);
  }
}
</style>
