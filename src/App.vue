<script setup>
import { RouterView } from 'vue-router';
import { onMounted } from 'vue';
import MainLayout from '@/layout/MainLayout.vue';
import { useApiDataStore } from '@/stores/apiDataStore.js';

const { callAPIs, state } = useApiDataStore();

onMounted(() => {
  callAPIs();
});
</script>

<template>
    <transition name="slide-down">
        <div class="loading" v-if="state.isLoading">
          <div>
            <div class="flex justify-center mb-4">
                <img src="/img/masjid.png" alt="" srcset="" class="w-24">
            </div>
            <p class="font-semibold">Konten sedang dimuat...</p>
          </div>
        </div>
    </transition>

  <MainLayout>
    <RouterView />
  </MainLayout>
</template>

<style scoped>
.loading {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: #111827;
    height: 100vh;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    z-index: 100;
}

.slide-down-enter-from {
    transform: translateY(-100%);
}
.slide-down-enter-to {
    transform: translateY(0);
}
.slide-down-enter-active {
    transition: transform 0.5s ease-out, opacity 0.5s ease-out;
}

.slide-down-leave-from {
    transform: translateY(0);
}
.slide-down-leave-to {
    transform: translateY(100%);
}
.slide-down-leave-active {
    transition: transform 0.5s ease-in, opacity 0.5s ease-in;
}
</style>
