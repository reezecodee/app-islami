<script setup>
import HeaderContent from '@/components/HeaderContent.vue';
</script>

<template>
    <div>
        <HeaderContent img="niat-sholat" text-title="Niat Sholat">
            <p class="mb-2">Niat yang benar menunjukkan bahwa kita melakukan sholat karena Allah SWT semata, bukan
                karena
                sebab-sebab lain seperti riya (ingin dipuji orang), sum'ah (ingin terkenal), atau karena paksaan.</p>
        </HeaderContent>

        <div class="flex justify-center gap-x-3 mt-7">
            <router-link to="/" class="w-full">
                <div
                    class="p-6 border-2 border-green-500 rounded-lg hover:bg-green-500 hover:bg-opacity-10 duration-300 mb-5 item">
                    <span class="text-xl text-start block font-semibold mb-3">Niat Sholat Wajib</span>
                    <h5
                        class="text-end text-3xl font-scheherazade-regular font-semibold block mb-3 font-scheherazade-regular">
                        صلوات فرض</h5>
                    <div class="text-sm">
                        <span class="text-start block font-medium leading-5 italic">Shalawat fardh</span>
                    </div>
                </div>
            </router-link>
            <router-link to="/" class="w-full">
                <div
                    class="p-6 border-2 border-green-500 rounded-lg hover:bg-green-500 hover:bg-opacity-10 duration-300 mb-5 item">
                    <span class="text-xl text-start block font-semibold mb-3">Niat Sholat Sunnah</span>
                    <h5 class="text-end text-3xl font-scheherazade-regular font-semibold block mb-3">صلوات سنة</h5>
                    <div class="text-sm">
                        <span class="text-start block font-medium leading-5 italic">Shalawat sunnah</span>
                    </div>
                </div>
            </router-link>
        </div>
    </div>
</template>

<style scoped></style>