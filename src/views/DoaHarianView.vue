<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const listItem = ref([]);
const textInput = ref(null);

onMounted(async () => {
    try {
        const response = await axios.get('https://islami-api.vercel.app/api/doa-harian');
        listItem.value = response.data.data;
    } catch (error) {
        window.location.href = '/error';
    }
});

onMounted(() => {
    window.addEventListener('keydown', handleKeyDown);
});

const handleKeyDown = (event => {
    if (event.ctrlKey && event.key === 'k') {
        event.preventDefault();
        textInput.value.focus();
    }
});

const setupSearch = () => {
    const inputElement = document.getElementById("search");
    const list = document.getElementById("list");
    const itemLists = list.getElementsByClassName("item");

    inputElement.addEventListener("input", function () {
        const searchText = inputElement.value.toLowerCase();
        for (const item of itemLists) {
            const listItemText = item.textContent.toLowerCase();
            if (listItemText.includes(searchText)) {
                item.style.display = "block";
            } else {
                item.style.display = "none";
            }
        }
    });
};

onMounted(() => {
    setupSearch();
});
</script>

<template>
    <div>
        <img src="https://www.svgrepo.com/show/317536/pray-day-islam.svg" class="w-20 inline-block" alt="" srcset="">
        <h1 class="text-4xl font-semibold my-4">Do'a Harian</h1>
        <p class="mb-2">"Berdoalah kepada Allah dan yakinlah bahwa doa kalian akan dikabulkan. Ketahuilah bahwa Allah
            tidak mengabulkan doa dari hati yang lalai dan tidak bersungguh-sungguh."</p>
        <div class="flex justify-center gap-x-3 mt-7">
            <input type="text" placeholder="Cari..." name="" id="search"
                class="border-[3.5px] border-gray-500 focus:outline-none focus:border-green-500 rounded-xl p-2.5 text-gray-800 w-full md:w-[30rem] font-medium placeholder:font-medium block"
                ref="textInput" autocomplete="off">
        </div>
        <div class="flex justify-center items-center gap-2 mt-6">
            <div
                class="py-0.5 px-2.5 text-xs bg-green-500 bg-opacity-30 border border-green-500 font-semibold rounded-md">
                Ctrl</div>
            <i class="fas fa-plus text-xs"></i>
            <div
                class="py-0.5 px-2.5 text-xs bg-green-500 bg-opacity-30 border border-green-500 font-semibold rounded-md">
                K</div>
        </div>
        <div class="mt-14 md:mt-20 mb-56" id="list">
            <div v-for="item in listItem" :key="item.urutan"
                class="p-6 border-2 border-green-500 rounded-lg w-full hover:bg-green-500 hover:bg-opacity-10 duration-300 mb-5 item">
                <span class="text-xl text-start block font-semibold mb-5">{{ item.urutan }}. {{ item.namaDoa
                    }}</span>
                <h5 class="text-end text-3xl font-semibold block mb-3">{{ item.arab }}</h5>
                <div class="text-sm">
                    <span class="text-start block font-medium leading-5">{{ item.arti }}</span>
                </div>
            </div>
        </div>
    </div>
</template>


<style scoped></style>