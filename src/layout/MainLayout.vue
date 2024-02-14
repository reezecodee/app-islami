<template>
    <Navbar></Navbar>
    <section id="content">
        <div class="px-3 md:px-14 container mx-auto flex justify-center mt-32 md:mt-20">
            <slot></slot>
        </div>
    </section>
</template>

<script setup>
import Navbar from '@/components/Navbar.vue';
</script>

<style scoped></style>