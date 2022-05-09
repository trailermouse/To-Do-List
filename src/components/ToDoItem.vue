<template>
  <li class="task-item">
    <div class="task-item__box">
      <input
        class="task-item__input"
        type="checkbox"
        @change="$emit('change-status', task.id)"
      />
      <div class="task-item__item">
        <div class="task-item__index">{{ index + 1 }}.</div>
        <div class="task-item__text" v-bind:class="{ done: task.completed }">
          {{ task.title | uppercase }}
        </div>
      </div>
    </div>
    <button class="task-item__button" @click="$emit('remove-task', task.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
    index: Number,
  },
  filters: {
    uppercase(value) {
      let newValue = value[0].toUpperCase() + value.slice(1);
      return newValue;
    },
  },
};
</script>

<style lang="scss" scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 1rem 2rem;
  background-color: $color-main-bg;
  border-radius: 1rem;
  font-size: 2rem;

  &:not(:last-child) {
    margin-bottom: 1.5rem;
  }

  &__box {
    display: flex;
    align-items: center;
    margin-right: 1rem;
  }

  &__input {
    margin-right: 1.4rem;
  }

  &__item {
    display: flex;
    width: 90%;
    align-items: center;
  }

  &__index {
    font-weight: 500;
    margin-right: 1rem;
  }

  &__button {
    background-color: $color-tertiary;
    color: $color-main-bg;
    border: none;
    padding: 0.5rem 1rem;
    font-size: 2rem;
    border-radius: 50%;
    cursor: pointer;

    &:hover {
      background-color: #f15874;
    }
  }
}

.done {
  text-decoration: line-through;
}

input[type="checkbox"] {
  appearance: none;
  background-color: $color-main-bg;
  font: inherit;
  color: $color-main-bg;
  width: 2.8rem;
  height: 2.8rem;
  border: 0.1rem solid $color-blue;
  border-radius: 6px;
  text-align: center;
}

input[type="checkbox"]::before {
  content: "👍";
  width: 2.8rem;
  height: 2.8rem;
  opacity: 0;
  transition: 0.3s all ease-in;
}

input[type="checkbox"]:checked {
  background-color: $color-blue;
}

input[type="checkbox"]:checked::before {
  opacity: 1;
}
</style>
