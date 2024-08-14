<script setup>
    import {ref} from 'vue'
    let sks = ref('');
    let tasks = ref([]);    
    let addTask = () => {
        console.log(sks.value);
        console.log('added');
        tasks.value.push({text: sks.value, done: false});
    };
    let removeTask = (task) => {
        tasks.value = tasks.value.filter((t) => t != task);
    }
</script>

<template>
    <form @submit.prevent="addTask()">
    <input v-model="sks" type="text" required placeholder="Enter new task...">
    <button>Add</button>
    </form>
    <ul v-for="task in tasks">
        <li :id="task.id">{{ task.text }}
        <button @click="removeTask(task)">X</button>
    </li>
        <br>
    </ul>
</template>

<style>
    input {
        border-radius: 10px;
        margin: 10px;
    }
    button {
        border-radius: 10px;
        border-width: 0px;
        size: 20px;
    }
</style>