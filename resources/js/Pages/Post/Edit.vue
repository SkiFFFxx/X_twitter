<script setup>
    import {Link} from '@inertiajs/vue3'
    import { router } from '@inertiajs/vue3'
    import {reactive} from "vue";
    import MainLayout from "@/Layouts/MainLayout.vue";




    const props = defineProps(['post'])



    const form = reactive({
        id: props.post.id,
        title: props.post.title,
        content: props.post.content,
    })


    function edit() {
        router.patch(route('post.update', form.id), {
            title: form.title,
            content: form.content,
        });
    }

    defineOptions({
        layout: MainLayout,
    });


</script>

<template>

            <h1 class="text-lg mb-4 text-center">Create</h1>
             <Link :href="route('post.index')" class="text-sm mb-4 text-sky-500 text-center">Back</Link>
            <form @submit.prevent="edit">
                <div class="mb-2">
                    <input v-model="form.title" class="w-96 rounded-full border-2 border-sky-500" type="text" placeholder="title">
                </div>
                <div class="mb-2">
                    <textarea v-model="form.content" class="w-96 rounded-full border-2 border-sky-500" type="text" placeholder="content"></textarea>
                </div>
                <div>
                    <button class="hover:bg-white hover:text-black block ml-auto p-2 w-32 border border-sky-500 rounded-full bg-sky-500 text-center text-white"
                            type="submit">Edit</button>
                </div>
            </form>


</template>

<style scoped>

</style>
