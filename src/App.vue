<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <Header theTitle="Vue To Due - Marco Chico"></Header>
    <TaskList theTitle="My Tasks" v-bind:taskList="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import TaskList from "./components/TaskList.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    TaskList,
  },

  data() {
    return {
      tasks: [
        { id: 1, title: "Learn HTML & CSS", completed: false },
        { id: 2, title: "Learn Javascript", completed: false },
        { id: 3, title: "Learn a JS Framework", completed: false },
        { id: 4, title: "Pass web Dev 2", completed: false },
      ],
    };
  },
  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/todos").then((res) => {
      this.tasks = res.data;
    });
  },
};
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

* {
  margin: 0;
  padding: 0;
}
</style>