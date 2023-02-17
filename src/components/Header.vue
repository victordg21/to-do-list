<script setup> 
    const props = defineProps(['tasksPending'])
</script>

<template>
    <header>
        <div class="container">
            <h1 class="my-tasks">Minhas Tarefas</h1>
            <p>
                Você possui {{props.tasksPending}} tarefas pendentes
            </p>
        </div>
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

.container{
    max-width: 960px;
    width: 100%;
    margin: 0 auto;
    }

@media (max-width: 767px){
    .container{
    max-width: 90%
    }
}

</style>