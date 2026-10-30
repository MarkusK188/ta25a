<script setup>
defineProps(['items', 'title']);


</script>

<template>
    <h1>{{ title }}</h1>
    <ul>
        <li v-for="item in items" :key="item.id" :class="{
            'has-text-danger': item.importance === 2,
            'has-text-warning': item.importance === 1,
            'has-text-success': item.importance === 0
        }">
            <input @click="" type="checkbox" v-model="item.isDone">
            {{ item.text + item.importance }}
        </li>
    </ul>
</template>