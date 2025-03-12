<script setup>
    import {Link} from '@inertiajs/vue3'
    import { router } from '@inertiajs/vue3'
    import {reactive} from "vue";
    import MainLayout from "@/Layouts/MainLayout.vue";

    const form = reactive({
        title: null,
        content: null,
    })

    function store() {
        router.post('/posts', form)
    }

    defineOptions({
        layout: MainLayout,
    });

    const props = defineProps(['errors'])

</script>

<template>

            <h1 class="text-lg mb-4 text-center">Create</h1>
             <Link :href="route('post.index')" class="text-sm text-sky-500 mb-4 text-center">Back</Link>
            <form @submit.prevent="store">
                <div class="mb-2">
                    <input v-model="form.title" class="w-96 rounded-full border-2 border-sky-500" type="text" placeholder="title">
                    <div v-if="errors.title" class="text-red-600 text-sm" >{{ errors.title }}</div>
                </div>
                <div class="mb-2">
                    <textarea v-model="form.content" class="w-96 rounded-full border-2 border-sky-500" type="text" placeholder="content"></textarea>
                    <div v-if="errors.content" class="text-red-600 text-sm" >{{ errors.content }}</div>
                </div>
                <div>
                    <button class="hover:bg-white hover:text-black block ml-auto p-2 w-32 border border-sky-500 rounded-full bg-sky-500 text-center text-white"
                            type="submit">Store</button>
                </div>
            </form>


</template>

<style scoped>

</style>
