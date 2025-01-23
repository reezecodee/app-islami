<script setup>
import Navbar from '@/components/Navbar.vue';
</script>

<template>
    <section id="content">
        <div
            class="px-3 md:px-10 container mx-auto h-auto flex justify-center mt-32 md:mt-20 text-center overflow-y-auto">
            <slot></slot>
        </div>
    </section>
    <Navbar></Navbar>
</template>

<style scoped></style>