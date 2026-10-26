<script setup>
import { computed, ref } from 'vue';
import ItemList from '../components/ItemList.vue';

let isPrimary = ref(true);
let text = ref("");

let i = 0;
let num = ref(0);
setInterval(() => {
    num.value++
}, 1000);

let activeImportance = 2

let items = ref([
    { id: i++, text: 'Piim', isDone: true, importance: 0 },
    { id: i++, text: 'Viin', isDone: false, importance: 0 },
    { id: i++, text: 'Õlu', isDone: true, importance: 1 },
    { id: i++, text: 'Peeter', isDone: false, importance: 0 },
    { id: i++, text: 'eee', isDone: false, importance: 2 },
]);
let newItem = ref('');

function add() {
    if (newItem.value.trim() !== '') {
        items.value.push({ id: i++, text: newItem.value.trim(), isDone: false, importance: activeImportance },);
        newItem.value = '';
    } else {
        alert("THIS THING EMPTY AF!!!"); //alert peatab kõik JavaScripti kui see ees on
        newItem.value = '';
    }
}

let doneItems = computed(() => items.value.filter(item => item.isDone));
let ToDoItems = computed(() => items.value.filter(item => !item.isDone));

let isOpen = ref(false)

</script>

<template>
    <div class="container content mt-3">
        {{ num }}
        <div class="field has-addons">
            <div class="control is-expanded">
                <input @keydown.enter="add" class="input" type="text" v-model="newItem"
                    placeholder="Enter new task here">
                <div class="dropdown" :class="{'is-active': isOpen }">
                    <div class="dropdown-trigger">
                        <button @click="isOpen = !isOpen" class="button" aria-haspopup="true" aria-controls="dropdown-menu">
                            <span>Dropdown button</span>
                            <span class="icon is-small">
                                <i class="fas fa-angle-down" aria-hidden="true"></i>
                            </span>
                        </button>
                    </div>
                    <div class="dropdown-menu" id="dropdown-menu" role="menu">
                        <div class="dropdown-content">
                            <a @click="activeImportance = 0"  class="dropdown-item"> Low importance </a>
                            <a @click="activeImportance = 1" class="dropdown-item"> Medium importance </a>
                            <a  @click="activeImportance = 2" class="dropdown-item "> High importance </a>
                        </div>
                    </div>
                </div>
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

<style></style>