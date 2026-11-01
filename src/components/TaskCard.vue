<template>
    <div>
        <h2>{{ title }}</h2>
        <p>{{ description }}</p>
    </div>
</template>

<script setup>
const props = defineProps({
    title: {
        type:String,
        required:true,
    },
    description: {
        type:String,
        required:true,
    },
    taskPoints: {
        type:Number,
        default:0,
    }
});
</script>