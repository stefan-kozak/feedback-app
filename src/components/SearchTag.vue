<template>
  <button
    ref="tag"
    @click="toggleTagFilter"
    :class="[
      isActive ? 'bg-blue-700 text-blue-50' : 'text-blue-700 bg-blue-50',
    ]"
    class="p-1 my-2 px-5 mx-1 rounded-full cursor-pointer font-bold"
  >
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    isActiveProp: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      isActive: this.isActiveProp,
    };
  },
  methods: {
    toggleTagFilter() {
      if (this.isActive === false) {
        this.isActive = true;
      } else {
        this.isActive = false;
      }

      this.$emit("toggle-tag-filter", this.$refs.tag.textContent.trim());
    },
  },
};
</script>

<style lang="scss" scoped></style>
