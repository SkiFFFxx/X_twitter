<script setup>
import {Link} from '@inertiajs/vue3'
import MainLayout from '@/Layouts/MainLayout.vue';


const props = defineProps(['post'])
console.log(props.post)

defineOptions({
    layout: MainLayout,
});



</script>

<template>

            <h1 class="text-lg mb-4">Post</h1>
            <div>
                <Link :href="route('post.index')" class="text-sm text-sky-500 mb-4 text-center">Back</Link>
            </div>
            <div class="mt-4" v-if="post">
                <div class="mb-12 p-2 border-t border-gray-500">
                    <div>id: {{ post.id}}</div>
                    <div>title: {{ post.title}}</div>
                    <div>content: {{ post.content}}</div>
                    <div class="text-sm text-right">{{ post.data}}</div>
                </div>
            </div >


</template>

<style scoped>

</style>
