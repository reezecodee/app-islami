<template>
    <MainLayout>
        <div>
            <h2 class="text-4xl font-semibold my-2">{{ surah.nama }}</h2>
            <h1 class="mb-1 text-4xl font-extrabold ">{{ surah.namaLatin }}</h1>
            <span class="font-semibold text-lg">{{ surah.arti }}. Surah ke-{{ surah.nomor }}. {{ surah.tempatTurun
                ==
                'Mekah' ? 'Makkiyyah' : 'Madaniyyah' }}</span>
            <div class="flex justify-center items-center gap-5 mt-4 font-semibold">
                <div class="flex items-center gap-2 cursor-pointer hover:text-green-500">
                    <i class="fas fa-volume-up"></i>
                    <span>Audio</span>
                </div>
                <div class="flex items-center gap-2 cursor-pointer hover:text-green-500">
                    <i class="fas fa-spell-check"></i>
                    <span>Latin</span>
                </div>
                <div class="flex items-center gap-2 cursor-pointer hover:text-green-500">
                    <i class="fas fa-book"></i>
                    <span>Tafsir</span>
                </div>
                <div class="flex items-center gap-2 text-black text-sm group">
                    <select name="" id="" class="py-1 px-3 rounded-md outline-none w-56 group-hover:cursor-pointer">
                        <option value="" selected>Pilih Qori'</option>
                        <option value="Abdullah-Al-Juhany">Abdullah-Al-Juhany</option>
                        <option value="Abdul-Muhsin-Al-Qasim">Abdul-Muhsin-Al-Qasim</option>
                        <option value="Abdurrahman-as-Sudais">Abdurrahman-as-Sudais</option>
                        <option value="Ibrahim-Al-Dossari">Ibrahim-Al-Dossari</option>
                        <option value="Misyari-Rasyid-Al-Afasi">Misyari-Rasyid-Al-Afasi</option>
                    </select>
                </div>
            </div>
            <div class="flex justify-between mt-7">
                <a :class="{ 'invisible': surah.nomor == 1 }" :href="'/baca-al-quran/surah/' + (surah.nomor - 1)"
                    class="p-2 rounded-md text-sm font-medium border-2 border-green-500 hover:bg-green-400 hover:bg-opacity-15"><i
                        class="fas fa-chevron-left"></i> Sebelumnya
                </a>
                <a :class="{ 'invisible': surah.nomor == 114 }" :href="'/baca-al-quran/surah/' + (surah.nomor + 1)"
                    class="p-2 rounded-md text-sm font-medium border-2 border-green-500 hover:bg-green-400 hover:bg-opacity-15">Selanjutnya
                    <i class="fas fa-chevron-right"></i></a>
            </div>
            <div class="mt-14 md:mt-20 mb-56 w-[60rem]">
                <div v-for="ayat in surah.ayat" :key="ayat.nomorAyat" class="mb-6 border-b-2 border-green-500">
                    <div
                        class="rounded-full bg-green-500 w-10 h-10 text-lg font-bold flex items-center justify-center mb-5">
                        {{
                            ayat.nomorAyat }}
                    </div>
                    <h2 class="text-end text-4xl block">{{ ayat.teksArab }}</h2>
                    <p class="text-end block italic text-green-500 mt-3">{{ ayat.teksLatin }}</p>
                    <p class="text-start mt-3">{{ ayat.teksIndonesia }}</p>
                    <div class="flex justify-end mt-3 mb-5">
                        <button
                            class="p-1 rounded-md text-xs font-medium border-2 border-green-500 hover:bg-green-400 hover:bg-opacity-15">Tandai
                            ayat</button>
                    </div>
                </div>
                <div class="flex justify-between mt-7">
                    <a :class="{ 'invisible': surah.nomor == 1 }" :href="'/baca-al-quran/surah/' + (surah.nomor - 1)"
                        class="p-2 rounded-md text-sm font-medium border-2 border-green-500 hover:bg-green-400 hover:bg-opacity-15"><i
                            class="fas fa-chevron-left"></i> Sebelumnya
                    </a>
                    <a :class="{ 'invisible': surah.nomor == 114 }" :href="'/baca-al-quran/surah/' + (surah.nomor + 1)"
                        class="p-2 rounded-md text-sm font-medium border-2 border-green-500 hover:bg-green-400 hover:bg-opacity-15">Selanjutnya
                        <i class="fas fa-chevron-right"></i></a>
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import MainLayout from '@/layout/MainLayout.vue';

const pathURL = ref(window.location.pathname.match(/\/surah\/(\d+)/));
const surah = ref([]);

onMounted(async () => {
    try {
        const response = await axios.get(`https://equran.id/api/v2/surat/${pathURL.value[1]}`);
        surah.value = response.data.data;
    } catch (error) {
        window.location.href = '/error';
    }
});
</script>

<style lang="scss" scoped></style>