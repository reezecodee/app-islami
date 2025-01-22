<script setup>
import { reactive, computed } from 'vue';
import { formattedDate, greeting } from '@/assets/indonesia-time.js';

const state = reactive({
    hours: 0,
    minutes: 0,
    seconds: 0,
});

function updateTime() {
    const now = new Date();
    state.hours = now.getHours();
    state.minutes = now.getMinutes();
    state.seconds = now.getSeconds();
}

setInterval(updateTime, 1000);

const strFormat = (time) => {
    return String(time).length < 2 ? "0" + time : time
}

const realtime = computed(() => {
    return `${strFormat(state.hours)}:${strFormat(state.minutes)}:${strFormat(state.seconds)}`;
});
</script>

<template>
    <div class="text-center">
        <img src="https://www.svgrepo.com/show/270068/mosque-islam.svg" class="w-20 inline-block" alt="" srcset="">
        <h1 class="text-4xl font-semibold my-4">Selamat {{ greeting() }}</h1>
        <p class="mb-2">"Maka, ingatlah kepada-Ku, Aku pun akan ingat kepadamu. <br class="hidden md:block">
            Bersyukurlah kepada-Ku dan janganlah kamu ingkar kepada-Ku."</p>
        <p class="mb-2"><strong>(QS. Al-Baqarah : 152)</strong></p>
        <time class="font-medium">{{ formattedDate }}, {{ realtime }}</time>
    </div>
</template>

<style scoped></style>