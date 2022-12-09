<template>
  <div class="container">
    <TitlePage />
    <newTask @newTask="addTask" />
    <transition>
      <TasksList  :tasks="tasks" @removeTask="deleteTask" />
    </transition>
    
  </div>
  <task-fotter />
</template>

<script>
import TasksList from "./components/TasksList.vue";
import newTask from "./components/NewTask.vue";
import TitlePage from "./components/TitlePage.vue";
import TaskFotter from "./components/TaskFotter.vue";

export default {
  name: "App",
  components: {
    TasksList,
    newTask,
    TitlePage,
    TaskFotter,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(task) {
      const newTask = {
        id: Math.random(),
        name: task.name,
        pending: true,
      };
      // const filterId =
      //   this.tasks.filter((task) => task.name = newTask.name).length === 0;
      newTask.id = Math.random();
      this.tasks.push(newTask);
    },

    deleteTask(task) {
      const i = this.tasks.indexOf(task)
      this.tasks.splice(i, 1)
    },
  },
  watch: {
    tasks: {
      deep: true, //monitora mudança no array e também nos estados internos
      handler() {
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      },
    },
  },
  created() {
    //leitura do local storage quando se inica a app
    const json = localStorage.getItem("tasks");
    const array = JSON.parse(json);
    this.tasks = Array.isArray(array) ? array : [];
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
</style>
<style>

* {
  margin: 0;
  padding: 0;
  font-family: "Roboto";
}
body {
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
}

.container {
  min-height: 85vh;
}
</style>
