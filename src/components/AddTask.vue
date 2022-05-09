<template>
  <form class="add-task" @submit.prevent="onSubmit">
    <input
      class="add-task__input"
      type="text"
      v-model="title"
      placeholder="Enter new task to do"
    />
    <button type="submit" class="add-task__button">Add</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTask = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };

        this.$emit("add-task", newTask);
        this.title = "";
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.add-task {
  max-width: 57rem;
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-bottom: 1.6rem;

  &__input {
    max-width: 30rem;
    width: 100%;
    border-radius: 0.8rem;
    border: 1px solid $color-light-grey;
    padding: 1rem;
    color: $color-text;
    font-size: 1.6rem;

    &::placeholder {
      color: $color-text;
      font-size: 1.6rem;
    }
  }

  &__button {
    max-width: 14rem;
    width: 100%;
    padding: 1rem 2.5rem;
    border: none;
    background-color: $color-blue;
    color: $color-main-bg;
    text-transform: uppercase;
    font-size: 1.8rem;
    font-weight: 500;
    letter-spacing: 0.1rem;
    border-radius: 0.8rem;
    cursor: pointer;

    &:hover {
      background-color: #3798e3;
    }
  }
}
</style>
