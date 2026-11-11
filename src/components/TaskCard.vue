<template>
    <div v-if="isEditing">
        <form @submit.prevent ="saveChages">
            <label for="title-${props.id}">Title: </label>
            <input type="text" required v-model="draft.title" id="title-${props.id}">

            <label for="description-${props.id}">Description: </label>
            <input type="text" required v-model="draft.description" id="description-${props.id}">

            <label for="status-${props.id}">Status: </label>
            <select type="dropdown" id="status-${props.id}">
                <option value="text">New</option>
                <option value="text">In Progress</option>
                <option value="text">Done</option>
            </select>

            <button type="submit">Save</button>
            <button @click="isEditing = false">Cancel</button>
        </form>
    </div>
    <div v-else>
        <h2 style="display: inline;">{{ id }}. </h2>
        <h2 style="display: inline;">{{ title }}</h2>
        <p>{{ description }}</p>
        <p>{{ status }}</p>
        <button @click="handleEdit">Edit</button>
    </div>
</template>

<script setup>
import {ref, reactive} from 'vue';
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
        required: true,
    },
    status: {
        type:String,
        required:true,
    },
});

const emit = defineEmits(['updated-task']);

const draft = reactive({
    title: '',
    description: '',
    status: ''
});
const isEditing = ref(false);

const handleEdit = () => {
    Object.assign(draft, {
        title : props.title,
        description : props.description,
        status : props.status
    });
    isEditing.value = true;
}

const saveChages = () => {
    emit('updated-task', {
        id: props.id,
        title: draft.title,
        description: draft.description,
        status: draft.status
    });
    isEditing.value = false;
}
</script>
