<template>
    <h1>Flex Board</h1>
    <TaskCard title="Basic project cleanup" description="Remove the default code present in the vue3 project"></TaskCard>
</template>


<script setup>
    import {ref} from 'vue';
    import TaskCard from './components/TaskCard.vue';
    const taskData = ref({
        title: "",
        description: "",
        AC: "",
        taskPoints: 0,
        RelatedTask: "",
    });
</script>
