<template>
    <form @submit.prevent="triggerEmit">
        <p>Task Title: </p>
        <input v-model="title" required type="text" placeholder="enter task title...">
        <p>Task Description: </p>
        <input v-model="description" required type="text" placeholder="enter task description...">
        <p>Task Status: </p>
        <label for="taskStatus"></label>
        <select id="taskStatus" v-model="status">
            <option value="New">New</option>
            <option value="In Progress">In Progress</option>
            <option value="Done">Done</option>
        </select>
        <br><br>
        <button type="submit" style="display: block;">Submit</button>
    </form>
</template>
<script setup>
    import {ref} from 'vue';
    const emit = defineEmits(['task-created']);
    const title = ref("");
    const description = ref("");
    const status = ref("New");

    const triggerEmit = () => {
        emit('task-created', {
            title: title.value,
            description: description.value,
            status: status.value
        });
        title.value = '';
        description.value = '';
        status.value = 'New';
    }

</script>