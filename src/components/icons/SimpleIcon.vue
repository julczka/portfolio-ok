<template>
  <div>
    <svg
      id="Layer_1"
      class="cls-1"
      data-name="Layer 1"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      @click="log"
    >
      <defs></defs>
      <path :d="iconPath" />
      <!-- <g id="Photoshop">
        <g id="_Group_" data-name=" Group ">
          <rect
            id="_Rectangle_"
            data-name=" Rectangle "
            class="cls-1"
            x="0.5"
            y="0.5"
            width="21"
            height="21"
          />

          <g id="_Group_2" data-name=" Group 2">
            <path
              id="_Path_"
              data-name=" Path "
              class="cls-1"
              d="M7.5,16.5v-9c2.53-.34,5,.13,5,2.5s-3.34,3.22-5,2.5"
              transform="translate(-1 -1)"
            />
            <path
              id="_Path_2"
              data-name=" Path 2"
              class="cls-1"
              d="M17.5,11c-.77-.73-3-.85-3,1s3,.9,3,3-2.37,1.6-3,1"
              transform="translate(-1 -1)"
            />
          </g>
        </g>
      </g> -->
    </svg>
  </div>
</template>
<script>
export default {
  props: {
    iconName: {
      type: String
    }
  },
  data() {
    return {
      icons: require("simple-icons")
    };
  },

  computed: {
    iconPath: function() {
      let iconObject = this.icons.get(this.iconName);
      return iconObject.path;
    }
  },

  methods: {
    log() {
      console.log(this.icons);
    }
  }
};
</script>

<style lang="scss" scoped>
svg {
  height: 70%;
  width: 70%;
}
.cls-1 {
  fill: var(--text-primary);
}
</style>
