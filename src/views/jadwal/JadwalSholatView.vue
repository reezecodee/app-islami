<script setup>
import HeaderContent from '@/components/HeaderContent.vue';
</script>

<template>
    <div>
        <HeaderContent img="jadwal-sholat" text-title="Jadwal Sholat">
            <p class="mb-2">"dan mohon lah pertolongan (kepada Allah) dengan sabar dan sholat. <br
                    class="hidden md:block">
                Dan (sholat) itu sungguh berat, kecuali bagi orang-orang yang khusyuk."</p>
            <div class="flex gap-x-3 mt-7">
                <input type="text" placeholder="Cari wilayah..." name="" id=""
                    class="border-[3.5px] border-gray-500 focus:outline-none focus:border-green-500 rounded-xl p-2.5 text-gray-800 w-full font-medium placeholder:font-medium">
            </div>
        </HeaderContent>

        <div class="mt-20 mb-56">
            <div class="text-5xl font-extrabold">
                Server Error 500
            </div>
        </div>
    </div>
</template>

<style scoped></style>