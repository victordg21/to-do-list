<script setup>
    const props = defineProps(['registerTasks', 'temporaryTasks','changeFilter','editTemporaryTasks'])
</script>

<template>
    <form @submit.prevent="props.registerTasks">
        <input :value="props.temporaryTasks" @change="props.editTemporaryTasks" required type="text" placeholder="Digite aqui a descrição da tarefa" class="put-tasks">
        <button type="submit">Cadastrar</button>
        <select @change="props.changeFilter">
            <option value="todas">Todas</option>
            <option value="finalizadas">Finalizadas</option>
            <option value="pendentes">Pendentes</option>
        </select>
    </form>
</template>

<style scoped>
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

@media (max-width: 767px){

    form{
        display: block;
    }
    .put-tasks{
        width: 300px;
        margin-bottom: 20px;
        align-items: center;
    }

}
</style>