<template>
    <form @submit.prevent="triggerEmit">
        <p>Task Title: </p>
        <input v-model="title" required type="text" placeholder="enter task title...">
        <p>Task Description: </p>
        <input v-model="description" required type="text" placeholder="enter task description...">
        <p>Task Status: </p>
        <input v-model="status" type="text" value="New">
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
        status.value = '';
    }

</script>