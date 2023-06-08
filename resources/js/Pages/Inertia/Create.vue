<script setup>
    import { reactive } from 'vue'
    import { Inertia } from '@inertiajs/inertia'
    import InputErrors from '@/Components/InputError.vue'

    defineProps({
        errors: Object
    })

    const form = reactive ({
        title: null,
        content: null
    })

    const submitFunction = () => {
        Inertia.post('/inertia', form)
    }



</script>

<template>
    <div v-if="Object.keys(errors).length"><ValidationErrors :errors="form.errors"/></div>
    <form @submit.prevent="submitFunction">
        <input name="title" type="text" v-model="form.title"><br>
        <InputErrors :message="errors.title"/>
        <input name="content" type="text" v-model="form.content"><br>
        <InputErrors :message="errors.content"/>
        <button>送信</button>
    </form>
</template>