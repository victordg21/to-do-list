<script setup>
import {reactive} from 'vue';

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
  <header>
    <h1 class="my-tasks">Minhas Tarefas</h1>
    <p>
      Você possui {{getPendingTasks().length}} tarefas pendentes
    </p>
  </header>
  <form @submit.prevent="registerTasks">
    <input :value="state.temporaryTasks" @change="event => state.temporaryTasks = event.target.value" required type="text" placeholder="Digite aqui a descrição da tarefa" class="put-tasks">
    <button type="submit">Cadastrar</button>
    <select @change="event => state.filter = event.target.value">
      <option value="odas">Todas</option>
      <option value="finalizadas">Finalizadas</option>
      <option value="pendentes">Pendentes</option>
    </select>
  </form>
  <ul>
    <li v-for="tasks in getFilterTasks()">
      <input @change="event => tasks.done = event.target.checked" :checked="tasks.done" :id="tasks.title" type="checkbox" class="checkbox">
      <label :class="{done: tasks.done}" :for="tasks.title">
        {{tasks.title}}
      </label>
    </li>
  </ul>
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

header{
  padding: 50px 0px;
  text-align: center;
  background-color: #094074;
  color: #fff;
}

.my-tasks{
  margin-bottom: 20px;
}

form{
  text-align: center;
  margin-top: 40px;
  justify-content: space-around;
}

input::placeholder{
  text-align: center;
}

.put-tasks{
  height: 35px;
  width: 500px;
  margin-right: 16px;
  border-radius: 6px;
}

button{
  height: 35px;
  font-weight: bold;
  background-color: #094074;
  color: #fff;
  margin-right: 16px;
  width: 100px;
  border-radius: 6px;
  cursor: pointer;
}

select{
  height: 35px;
  width: 100px;
  font-weight: bold;
  border-radius: 6px;
  cursor: pointer;
}

ul{
  list-style: none;
  margin-top: 20px;
}

li{
  border: 1px solid #000;
  width: 732px;
  border-radius: 6px;
  height: 40px;
  margin: 0 auto;
  padding-top: 12px;
  padding-left: 8px;
  margin-bottom: 16px;
}

label{
  font-weight:600;
  margin-left: 4px;
}

.done{
  text-decoration: line-through;
}

</style>
