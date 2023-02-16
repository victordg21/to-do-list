<script setup> 
    const props = defineProps(['tasksPending'])
</script>

<template>
    <header>
    <h1 class="my-tasks">Minhas Tarefas</h1>
    <p>
        Você possui {{props.tasksPending}} tarefas pendentes
    </p>
    </header>
</template>

<style scoped>
    header{
    padding: 50px 0px;
    text-align: center;
    background-color: #094074;
    color: #fff;
}

.my-tasks{
    margin-bottom: 20px;
}

</style>