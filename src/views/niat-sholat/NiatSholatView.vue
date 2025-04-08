<script setup>
import HeaderContent from '@/components/HeaderContent.vue';
</script>

<template>
    <div>
        <HeaderContent img="niat-sholat" text-title="Niat Sholat" :keyCaps="false">
            <p class="mb-2">Niat yang benar menunjukkan bahwa kita melakukan sholat karena Allah SWT semata, bukan
                karena
                sebab-sebab lain seperti riya (ingin dipuji orang), sum'ah (ingin terkenal), atau karena paksaan.</p>
        </HeaderContent>

        <div class="mt-10 mb-32">
            <div class="flex justify-center">
                <router-link to="/jadwal-sholat">
                    <button
                        class="bg-green-500 hover:bg-green-600 duration-300 p-2 text-white font-medium rounded-md mt-3">
                        <i class="fas fa-search"></i> Cek Jadwal Sholat
                    </button>
                </router-link>
            </div>

            <div class="flex flex-wrap md:flex-nowrap justify-center gap-x-3 mt-7">
                <router-link to="/niat-sholat/daftar/wajib" class="w-full">
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
                <router-link to="/niat-sholat/daftar/sunnah" class="w-full">
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
    </div>
</template>

<style scoped></style>