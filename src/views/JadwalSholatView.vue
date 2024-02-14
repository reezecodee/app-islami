<template>
    <MainLayout>
        <div>
            <img src="https://www.svgrepo.com/show/317542/pray-night-islam.svg" class="w-20 inline-block" alt="" srcset="">
            <h1 class="text-4xl font-semibold my-4">Jadwal Sholat</h1>
            <p class="mb-2">"dan mohon lah pertolongan (kepada Allah) dengan sabar dan sholat. <br class="hidden md:block">
                Dan (sholat) itu sungguh berat, kecuali bagi orang-orang yang khusyuk."</p>
            <form action="" method="post" class="flex gap-x-3 mt-7">
                <input type="text" placeholder="Cari wilayah..." name="" id=""
                    class="border-[3.5px] border-gray-500 focus:outline-none focus:border-green-500 rounded-xl p-2.5 text-gray-800 w-full font-medium placeholder:font-medium">
                <button class="bg-green-500 hover:bg-green-600 duration-300 py-2.5 px-5 rounded-xl" type="submit">
                    Search</button>
            </form>

            <div class="mt-20 mb-56">
                <div class="text-5xl font-extrabold">
                    Server Error 500
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<script setup>
import MainLayout from '@/layout/MainLayout.vue';


</script>

<style scoped></style>