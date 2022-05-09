<template>
  <div class="sort-tasks">
    <select class="sort-tasks__list">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="in-progress">In progress</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    filter: {
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
.sort-tasks {
  width: 57rem;
  display: flex;
  justify-content: flex-end;

  &__list {
    max-width: 14rem;
    width: 100%;
    border-radius: 0.8rem;
    border: 1px solid $color-light-grey;
    padding: 1rem;
    color: $color-text;
    font-size: 1.6rem;
  }
}
</style>
