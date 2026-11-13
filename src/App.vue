<template>
    <h1 style="padding-bottom: 30px;">Flex Board</h1> 
    <Stats :taskData="taskData"></Stats>
    <p v-if="taskData.length === 0">No tasks available</p>
    <TaskCard
        v-for="task in taskData"
        :id="task.id"
        :key="task.id"
        :title="task.title"
        :description="task.description"
        :status="task.status"
        @task-updated="updateTask"
        @task-deleted="deleteTask"
    />
    <TaskForm @task-created="receiveTask"></TaskForm>
</template>

<script setup>
    import {ref} from 'vue';
    import TaskCard from './components/TaskCard.vue';
    import Stats from './components/Stats.vue';
    import TaskForm from './components/TaskForm.vue';

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

    const receiveTask = (task) => {
        const taskId = Math.max(
            0,
            ...taskData.value.map(task => task.id)
        ) + 1;
        const newTask = {...task, id: taskId};
        taskData.value.push(newTask);
    }

    const updateTask = (updatedTask) => {
        taskData.value = taskData.value.map(task =>
            task.id === updatedTask.id ? updatedTask : task
        );
    }

    const deleteTask = (id) => {
        return taskData.value = taskData.value.filter(task => 
            task.id !== id
        );
    }
</script>
