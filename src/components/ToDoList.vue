<template>
  <div class="wrapper">
    <ul>
      <ToDoItem
        v-for="(task, i) of tasks"
        :key="task"
        v-bind:task="task"
        v-bind:index="i"
        @remove-task="removeTask"
        @change-status="changeStatus"
      />
    </ul>
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem.vue";

export default {
  props: ["tasks"],
  components: {
    ToDoItem,
  },
  methods: {
    removeTask(id) {
      this.$emit("remove-task", id);
    },

    changeStatus(id) {
      this.$emit("change-status", id);
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  max-width: 60rem;
  width: 100%;
}

ul {
  width: 100%;
  padding: 2.5rem;
  border-radius: 2rem;
  list-style: none;
  background-color: $color-secondary;
}
</style>
