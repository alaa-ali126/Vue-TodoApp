<template>
  <TasksListVue></TasksListVue>
</template>

<style></style>

<script>
import TasksListVue from "./components/TasksList.vue";
export default {
  components: {
    TasksListVue,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;900&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Nunito", sans-serif;
  font-size: 14px;
  color: #555;
  background-color: #f0efe9;
}
</style>
