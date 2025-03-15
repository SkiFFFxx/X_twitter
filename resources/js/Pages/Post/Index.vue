<script setup>
import {Link, router} from '@inertiajs/vue3'
import MainLayout from "@/Layouts/MainLayout.vue";


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



</script>

<template>

            <h1 class="text-lg mb-4 ">Posts</h1>
            <div>
                <Link :href="route('post.create')" class="hover:bg-white hover:text-black block p-2 w-32 border border-sky-500 rounded-full bg-sky-500 text-center text-white">Add Post</Link>
            </div>
            <div class="mt-4 " v-if="posts">
                <div class=" p-2 border-t border-gray-500" v-for="post in posts">

                    <Link class="text-2xl text-sky-500 hover:text-sky-800" :href="route('post.show', post.id)" >{{ post.title}}</Link>
                    <div>{{ post.content}}</div>

                    <div class="flex gap-4 justify-end mt-2">
                        <Link class="text-sky-500 hover:text-sky-800" :href="route('post.show', post.id)">Show</Link>
                        <Link class="text-sky-500 hover:text-sky-800" :href="route('post.edit', post.id)">Edit</Link>
                        <p
                            @click="deletePost(post.id)"
                            class="cursor-pointer text-red-500 hover:text-red-800"
                        >
                            Delete
                        </p>
                    </div>
                    <div class="text-sm flex justify-between">
                        <span>#{{ post.id }}</span>
                        <span>{{ post.data }}</span>
                    </div>
                </div>
            </div >


</template>

<style scoped>

</style>
