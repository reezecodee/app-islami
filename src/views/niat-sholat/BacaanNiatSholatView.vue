<script setup>
import { ref, onMounted, computed } from 'vue'
import { useApiDataStore } from '@/stores/apiDataStore.js'
import { useRouter } from "vue-router"
import HeaderContent from '@/components/HeaderContent.vue';

const type = ref('')
const router = useRouter()
const pathMatch = window.location.pathname.match(/\/daftar\/(\w+)/)
const { state } = useApiDataStore()

const typeKey = pathMatch ? pathMatch[1] : null

onMounted(() => {
    if (typeKey === 'wajib') {
        type.value = 'Wajib'
    } else if (typeKey === 'sunnah') {
        type.value = 'Sunnah'
    } else {
        router.push('/niat-sholat')
    }
})

const listItem = computed(() => {
    return typeKey === 'wajib' ? state.sholatWajib :
        typeKey === 'sunnah' ? state.sholatSunnah : []
})
</script>

<template>
    <div>
        <HeaderContent img="niat-sholat" :text-title="`Niat Sholat ${type}`" :keyCaps="false">
            <p class="mb-2">Berikut ini adalah daftar niat sholat {{ typeKey }} yang bisa kita ketahui dan memahami bacaanya.</p>
        </HeaderContent>

        <div class="mt-14 md:mt-20 mb-56 w-full md:w-[60rem]">
            <div v-for="(item, index) in listItem" :key="item.namaSholat" class="mb-6 border-b-2 border-green-500">
                <div class="flex justify-start items-center gap-3 mb-5">
                    <div
                        class="rounded-full bg-green-500 px-2 py-2 w-10 h-10 text-lg font-bold flex items-center justify-center ">
                        {{ index + 1 }}
                    </div>
                    <p v-if="typeKey === 'wajib'" class="font-semibold text-lg text-start">{{ item.niatSholat }} ({{ item.namaSholat }})</p>
                    <p v-if="typeKey === 'sunnah'" class="font-semibold text-lg text-start"> Sholat Sunnah {{ item.namaSholat }}</p>
                </div>
                <h2 class="text-end text-4xl block font-scheherazade-regular leading-loose">{{ item.teksArab }}</h2>
                <p class="text-end block italic text-green-500 mt-3">{{ item.teksLatin
                }}
                </p>
                <p class="text-start mt-3 mb-3">{{ item.artinya }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped></style>