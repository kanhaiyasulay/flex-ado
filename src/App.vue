<template>
    <h1 style="padding-bottom: 30px;">Flex Board</h1> 
    <div v-for="task in taskData">
        <TaskCard :id="task.id" :title="task.title" :status="task.status"></TaskCard>
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
            status: "In Progress"
        },
        {
            id: 2,
            title: "Create Dashboard",
            status: "New"
        },
        {
            id: 3,
            title: "Fix Navbar Bug",
            status: "Done"
        },
        {
            id: 4,
            title: "Add User Profile",
            status: "New"
        }
    ]);
</script>
