<script setup>
import { ref } from 'vue';

const isToggled = ref(false);

const toggleGif = () => {
    isToggled.value = !isToggled.value;
};
</script>

<template>
    <div class="w-96 mx-auto pt-8">
        <img
            :src="isToggled
                ? 'https://media1.tenor.com/m/lUU2wbgHrioAAAAC/konata-luckystar.gif'
                : 'https://media1.tenor.com/m/hvU8c92x3qcAAAAC/anime.gif'"
            alt="Funny GIF"
            class="w-full h-40 object-cover mb-4 cursor-pointer"
            @click="toggleGif"
        />
        <h1 class="text-lg mb-8">My Posts Site</h1>
        <slot />
    </div>
</template>

<style scoped>
</style>
