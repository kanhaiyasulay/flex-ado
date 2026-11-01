<template>
    <div>
        <p>{{ id }}</p>
        <h2>{{ title }}</h2>
        <p>{{ status }}</p>
    </div>
</template>

<script setup>
const props = defineProps({
    id: {
        type: Number,
        required: true,
    },
    title: {
        type:String,
        required:true,
    },
    status: {
        type:String,
        required:true,
    },
});
</script>