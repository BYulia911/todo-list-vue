<template>
  <select name="filter" id="filter" v-model="selected" @change="selectedFilter">
    <option v-for="option in options" :key="option">{{ option }}</option>
  </select>
</template>

<script>
export default {
  emits: ["filter"],
  data() {
    return {
      selected: "All",
      options: ["All", "Completed", "Not completed"],
    };
  },
  methods: {
    selectedFilter() {
      this.$emit("filter", this.selected);
    },
  },
};
</script>
