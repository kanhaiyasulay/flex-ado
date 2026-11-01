<template>
    <h1 style="padding-bottom: 30px;">Flex Board</h1> 
    <p v-if="taskData.length === 0">No tasks available</p>
    <div v-for="task in taskData">
        <TaskCard :id="task.id" :key="task.id" :title="task.title" :description="task.description" :status="task.status"></TaskCard>
        <br>
    </div>
</template>

<script setup>
    import {ref} from 'vue';
    import TaskCard from './components/TaskCard.vue';
    const taskData = ref([
        {
            id: 1,
            title: "Implement Login API",
            description: "you would need to dig in BE",
            status: "In Progress"
        },
        {
            id: 2,
            title: "Create Dashboard",
            description: "Use the existing DB",
            status: "New"
        },
        {
            id: 3,
            title: "Fix Navbar Bug",
            description: "Fix the weired line rendering",
            status: "Done"
        },
        {
            id: 4,
            title: "Add User Profile",
            description: "Make sure to handle duplication case",
            status: "New"
        }
    ]);
</script>
