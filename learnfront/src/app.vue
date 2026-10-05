<script setup>
import {computed, ref} from 'vue';

    let isPrimary = ref(true);
    let text = ref("");
    let i = 0;

    let items = ref([
        {id:i++, text:'Piim', isDone: true},
        {id:i++, text:'Viin', isDone: false},
        {id:i++, text:'Õlu', isDone: true},
        {id:i++, text:'Peeter', isDone: false},
        {id:i++, text:'eee', isDone: false},
        ]);
    let newItem = ref('');

    function add(){
        if(newItem.value.trim() !== '') {
            items.value.push({id:i++, text:newItem.value.trim(), isDone: false},);
            newItem.value = '';
        } else {console.log("THIS SHIT EMPTY AF!!!");
             newItem.value = '';
        }
    }

    let doneItems = computed(() => items.value.filter(item => item.isDone));
    let ToDoItems = computed(() => items.value.filter(item => !item.isDone));
</script>

<template>
    <div class="container content mt-3">
        <div class="field has-addons">
             <div class="control is-expanded">
                <input @keydown.enter="add" class="input" type="text" v-model="newItem" placeholder="Find a repository">
            </div>
            <div class="control">
                <button @click="add" class="button is-primary">
                    Add
                </button>
            </div>
        </div>
        <h1>All items</h1>
        <ul>
            <li v-for="item in items" :key="item.id">
                {{ item.text }}
                <input @click="" type="checkbox" v-model="item.isDone">
            </li>   
        </ul>

         <h1>Done items</h1>
        <ul>
            <li v-for="item in doneItems" :key="item.id">
                {{ item.text }}
                <input @click="" type="checkbox" v-model="item.isDone">
            </li>   
        </ul>

        <h1>ToDo items</h1>
        <ul>
            <li v-for="item in ToDoItems" :key="item.id">
                {{ item.text }}
                <input @click="" type="checkbox" v-model="item.isDone">
            </li>   
        </ul>
        
    </div>
    

</template>

<style>

</style>