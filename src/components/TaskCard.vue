<template>
    <div>
        <h2 style="display: inline;">{{ id }}. </h2>
        <h2 style="display: inline;">{{ title }}</h2>
        <p>{{ description }}</p>
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
    description: {
        type:String,
        required: false,
    },
    status: {
        type:String,
        required:true,
    },
});
</script>