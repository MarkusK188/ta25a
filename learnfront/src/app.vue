<script setup>
import {computed, ref} from 'vue';
import ItemList from './ItemList.vue';

    let isPrimary = ref(true);
    let text = ref("");
    let i = 0;
let num = ref(0);
setInterval(() => {
    num.value++
}, 1000);
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
        } else {alert("THIS SHIT EMPTY AF!!!"); //alert peatab kõik JavaScripti kui see ees on
             newItem.value = '';
        }
    }

    let doneItems = computed(() => items.value.filter(item => item.isDone));
    let ToDoItems = computed(() => items.value.filter(item => !item.isDone));
</script>

<template>
    <div class="container content mt-3">
        {{ num }}
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

        <ItemList :items="items" title="All items"></ItemList>
        <ItemList :items="doneItems" title="Done Items"></ItemList>
        <ItemList :items="ToDoItems" title="ToDo Items"></ItemList>
    </div>
    

</template>

<style>

</style>