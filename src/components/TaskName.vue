<template>
  <div class="task">
    <p :class="stateClass" @click="taskClone.pending = !taskClone.pending">{{task.name}}</p>
    <button :class="stateClass" @click="$emit('removeTask', task)"><img src="../assets/icon.png"/></button>
  </div>
  
</template>

<script>

export default {
    props: {task: Object},
    data() {
      return {
        taskClone: this.task
      }
    },
    computed: {
      stateClass(){
        return{
          pending: this.task.pending,
          done: !this.task.pending,
        }
      }
    }
}

</script>

<style>
.task{
  display: flex;
  justify-content: center;
  margin: 1em 0em;
}
.pending{
 color: black;

}

.done{
  opacity: 0.3;
  text-decoration: line-through;
}

.task button {
  border-top-right-radius: 15px;
  border-bottom-right-radius: 15px;
  border: 1px solid #fff;
  width: 5em;
  background-color: rgb(84, 135, 192);
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}

.task img {
  width: 15px;
  height: 20px;
}

.task p {
  width: 40%;
  border-top-left-radius: 15px;
  border-bottom-left-radius: 15px;
  border: 1px solid #fff;
  height: 1.5em;
  display: flex;
  align-items: center;
  background-color: #fff;
  padding: 0.1em;
}
</style>