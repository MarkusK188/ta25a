<script setup>
import { ref } from 'vue';
import Tabs from './components/Tabs.vue';

let tabTitles = ref([
    'Item1',
    'Item2',
    'Item3',
    'Item4',
]);
let activeTab = ref(0);
let contents = [
    'Content1',
    'Content2', 
    'Content3', 
    'Content4',  
];

</script>

<template>
    <Tabs :titles="tabTitles" :active="activeTab" @change="activeTab= $event"></Tabs>
    <div class="container content mt-3">
        <h1>{{ contents[activeTab] }}</h1>
    </div>

</template>

<style></style>