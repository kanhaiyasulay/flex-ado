<template>
    <p>Total Tasks = {{ totTasks }}</p>
    <p>New Tasks = {{ newTasks }}</p>
    <p>In Progress = {{ inProgress }}</p>
    <p>Completed = {{ completed }}</p>
</template>

<script setup>
import { computed } from 'vue';

    const props = defineProps({
        taskData: {
            type: Array,
            required: true,
        }
    });

    const totTasks = computed(() => {
        return props.taskData.length;
    });

    const newTasks = computed(() => {
        return props.taskData.filter(task => task.status === "New").length;
    });

    const inProgress = computed(() => {
        return props.taskData.filter(task => task.status === "In Progress").length;
    });

    const completed = computed(() => {
        return props.taskData.filter(task => task.status === "Done").length;
    });
</script>