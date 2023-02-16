<script setup>
    const props = defineProps(['tasks'])
</script>

<template>
    <ul>
    <li v-for="tasks in props.tasks">
        <input @change="event => tasks.done = event.target.checked" :checked="tasks.done" :id="tasks.title" type="checkbox" class="checkbox">
        <label :class="{done: tasks.done}" :for="tasks.title">
        {{tasks.title}}
        </label>
    </li>
    </ul>
</template>

<style scoped>
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