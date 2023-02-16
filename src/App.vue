<script setup>
import {reactive} from 'vue';
import Header from './components/Header.vue'
import Forms from './components/Forms.vue'
import TasksList from './components/TasksList.vue'

const state = reactive({

  filter: 'todas',
  temporaryTasks: '',
    tasks:[
      {
        title: 'Estudar Física',
        done: false
      },
      {
        title: 'Lavar a Roupa',
        done: true
      },
      {
        title: 'Comprar verduras',
        done: false
      }
    ]
  })

  const getPendingTasks = () => {
    return state.tasks.filter( tasks => !tasks.done)
  }

  const getDoneTasks = () => {
    return state.tasks.filter( tasks => tasks.done)
  }

  const getFilterTasks = () => {
    const{filter} = state;

    switch(filter){
      case 'pendentes':
        return getPendingTasks()
      case 'finalizadas':
        return getDoneTasks()
      default:
        return state.tasks

    }
  }

const registerTasks = () => {
  const newTasks = {
    title: state.temporaryTasks,
    done: false,
  }
  state.tasks.push(newTasks)
  state.temporaryTasks = ''
}
</script>

<template>
  <div class="container">
    <Header :tasks-pending="getPendingTasks().length" />
    <Forms :change-filter="event => state.filter = event.target.value" :temporary-tasks="state.temporaryTasks" :edit-temporary-tasks="event => state.temporaryTasks = event.target.value" :register-tasks="registerTasks"  />
    <TasksList :tasks="getFilterTasks()" />
  </div>
</template>

<style scoped>

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}
.container{
  max-width: 960px;
  width: 100%;
  margin: 0 auto;
}
</style>
