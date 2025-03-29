<script setup>
import {Link, router} from '@inertiajs/vue3';
import MainLayout from "@/Layouts/MainLayout.vue";
import { ref } from 'vue';

const props = defineProps({
    posts: Array
})

defineOptions({
    layout: MainLayout,
});

function deletePost(id) {
    if (confirm('Are you sure you want to delete this post?')) {
        router.delete(route('post.delete', id));
    }
}

const activeDropdown = ref(null);

function toggleDropdown(id) {
    activeDropdown.value = activeDropdown.value === id ? null : id;
}
</script>

<template>

    <h1 class="text-lg mb-4 ">Posts</h1>
    <div>
        <Link :href="route('post.create')" class="hover:bg-white hover:text-black block p-2 w-32 border border-sky-500 rounded-full bg-sky-500 text-center text-white">Add Post</Link>
    </div>
    <div class="mt-4 " v-if="posts">
        <div class="p-2 border-t border-gray-500" v-for="post in posts">
            <div class="flex justify-between items-center">
                <Link class="text-2xl text-sky-500 hover:text-sky-800" :href="route('post.show', post.id)">
                    {{ post.title }}
                </Link>

                <div class="relative">
                    <div @click="toggleDropdown(post.id)" class="cursor-pointer text-sky-500 hover:text-sky-800">&#x22EE;</div>
                    <div v-if="activeDropdown === post.id"
                         class="absolute right-0 top-6 bg-white shadow-md border rounded-md w-24 z-10">
                        <Link class="block p-2 text-sky-500 hover:bg-sky-100" :href="route('post.show', post.id)">Show</Link>
                        <Link class="block p-2 text-sky-500 hover:bg-sky-100" :href="route('post.edit', post.id)">Edit</Link>
                        <p @click="deletePost(post.id)" class="block p-2 cursor-pointer text-red-500 hover:bg-red-100">Delete</p>
                    </div>
                </div>
            </div>

            <div>{{ post.content }}</div>


            <div class="text-sm flex justify-between">
                <span>#{{ post.id }}</span>
                <span>{{ post.data }}</span>
            </div>
        </div>
    </div>
</template>

<style scoped>
</style>
