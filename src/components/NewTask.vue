<template>
  <div class="addTask">
    <input type="text" placeholder="Digite sua tarefa" v-model="name"/>
    <button class="btn" @click="add">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
    };
  },
  methods: {
    add() {
      this.$emit("newTask", {name: this.name});
      this.name = ''
    },
  },
};
</script>

<style>
.addTask{
  display: flex;
  justify-content: center;
  margin-bottom: 2em;
}
.addTask input {
  width: 40%;
  height: 2.5em;
  border-top-left-radius: 15px;
  border-bottom-left-radius: 15px;
  border: 1px solid #fff;
  margin-top: 1.5em;
  padding: .2em;
}

.addTask .btn{
  margin-top: 1.5em;
  border-top-right-radius: 15px;
  border-bottom-right-radius: 15px;
  border: 1px solid #fff;
  width: 5em;
  background-color: rgb(84, 135, 192);
  color: #fff
};
</style>