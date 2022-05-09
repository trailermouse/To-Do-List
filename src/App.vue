<template>
  <div id="app" class="app">
    <h1 class="app__main-heading">To-Do List</h1>
    <AddTask @add-task="addTask" />
    <LoaderTasks v-if="loading" />
    <ToDoList
      v-else-if="tasks.length"
      v-bind:tasks="tasks"
      @remove-task="removeTask"
      @change-status="changeStatus"
    />
    <div class="app__message" v-else>Nothing to do! Add a new task ☝</div>
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList.vue";
import AddTask from "./components/AddTask.vue";
import LoaderTasks from "./components/LoaderTasks.vue";

export default {
  name: "App",
  data() {
    return {
      tasks: [],
      loading: true,
    };
  },
  components: {
    ToDoList,
    AddTask,
    LoaderTasks,
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos/?_limit=3")
      .then((response) => response.json())
      .then((json) => {
        this.tasks = json;
        this.loading = false;
      });
  },
  methods: {
    removeTask(id) {
      this.tasks = this.tasks.filter((t) => t.id !== id);
    },

    changeStatus(id) {
      this.tasks.forEach((t) => {
        if (t.id === id) {
          t.completed = !t.completed;
          console.log(t.completed);
        }
      });
    },

    addTask(newTask) {
      this.tasks.push(newTask);
    },
  },
};
</script>

<style lang="scss">
$this: &;

.app {
  max-width: $max-content-xl;
  margin: 0 auto;
  font-family: $font, Arial, Helvetica, sans-serif;
  font-size: 1.6rem;
  color: $color-text;
  background-color: $color-main-bg;
  margin-top: 9rem;
  display: flex;
  flex-direction: column;
  align-items: center;

  &__main-heading {
    color: $color-heading;
    border: none;
    text-transform: uppercase;
    font-weight: 700;
    font-size: 8.4rem;
    letter-spacing: 0.2rem;
    margin-bottom: 5rem;
  }

  &__message {
    margin-top: 5rem;
    font-size: 2.8rem;
    font-weight: 400;
  }
}
</style>
