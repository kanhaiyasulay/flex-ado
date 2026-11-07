<template>
    <article>
        <template v-if="isEditing">
            <form @submit.prevent="saveChanges">
                <h2>{{ id }}. Edit task</h2>
                <label :for="`task-title-${id}`">Title</label>
                <input :id="`task-title-${id}`" v-model="draft.title" required type="text">

                <label :for="`task-description-${id}`">Description</label>
                <textarea :id="`task-description-${id}`" v-model="draft.description" required></textarea>

                <label :for="`task-status-${id}`">Status</label>
                <select :id="`task-status-${id}`" v-model="draft.status" required>
                    <option value="New">New</option>
                    <option value="In Progress">In Progress</option>
                    <option value="Done">Done</option>
                </select>

                <button type="submit">Save</button>
                <button type="button" @click="isEditing = false">Cancel</button>
            </form>
        </template>
        <template v-else>
            <h2 style="display: inline;">{{ id }}. </h2>
            <h2 style="display: inline;">{{ title }}</h2>
            <p>{{ description }}</p>
            <p>{{ status }}</p>
            <button type="button" @click="editHandler">Edit</button>
        </template>
    </article>
</template>

<script setup>
import { reactive, ref } from 'vue';

const props = defineProps({
    id: {
        type: Number,
        required: true,
    },
    title: {
        type: String,
        required: true,
    },
    description: {
        type: String,
        required: true,
    },
    status: {
        type: String,
        required: true,
    },
});

const emit = defineEmits(['task-updated']);
const isEditing = ref(false);
const draft = reactive({
    title: '',
    description: '',
    status: '',
});

const editHandler = () => {
    Object.assign(draft, {
        title: props.title,
        description: props.description,
        status: props.status,
    });
    isEditing.value = true;
};

const saveChanges = () => {
    emit('task-updated', {
        id: props.id,
        title: draft.title,
        description: draft.description,
        status: draft.status,
    });
    isEditing.value = false;
};
</script>
