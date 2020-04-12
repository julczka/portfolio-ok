<template>
  <div class="button">
    {{ text }}
  </div>
</template>

<script>
export default {
  name: "button-component",
  props: {
    text: {
      type: String
    },
    outline: {
      type: Boolean
    }
  }
};
</script>

<style lang="scss" scoped>
.button {
  border: 1.5px solid var(--bg-secondary);
  color: var(--text-primary);
  font-size: 1rem;
  padding: 0.5em;
  min-width: 6em;
}
</style>
