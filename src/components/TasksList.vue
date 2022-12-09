<template>
    <ul>
    <transition-group name="slide">
        <TaskName v-for="task in tasks" :key="task.id" :task="task" @removeTask="$emit('removeTask', task)" ></TaskName> 
    </transition-group>
    
  
    </ul>
</template>

<script>
import 'animate.css';
import TaskName from './TaskName.vue';

export default {
    components: {
    TaskName,
},
    props: {tasks: Array}
}
</script>

<style>

@keyframes slide-in {
	from{transform: translateY(40px);}
	to{transform: translateY(0);}
}

@keyframes slide-out {
	from{transform: translateY(0);}
	to{transform: translateY(-60px);}
}

.slide-enter-active {
	animation: slide-in 2s ease;
}

.slide-leave-active {
	transition: opacity 0.5s ease;
}

.slide-leave-to {
    opacity: 0;
}
</style>