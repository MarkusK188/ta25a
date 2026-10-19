<script setup>
    import {ref} from 'vue';
    import Modal from '../components/Modal.vue';
    import ImgModal from '../components/ImgModal.vue';

    let modal1Open = ref(false);
    let modal2Open = ref(false);
    let modal3Open = ref(false);

   


    let answer = modal1Open ? 'Modal is active' : 'Modal'; //shorthand if statement
</script>

<template>

    <div class="container content mt-3">
        <button class="button is-primary" @click="modal1Open = true">Open Modal 1</button>
       <Modal 
       :active="modal1Open"
        @close="modal1Open = false" 
        url="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSQmfpMMAd9KJwKALHtFUQWOH0tVzYRULANUpHwHs3VE-awHPfWy3Mu6N4&s=10">
        <div class='box'>I'm in a box.</div>
    </Modal>
    </div>

     <div class="container content mt-3">
        <button class="button is-success" @click="modal2Open = true">Open Modal 2</button>
       <ImgModal :active="modal2Open" @close="modal2Open = false" url="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSQmfpMMAd9KJwKALHtFUQWOH0tVzYRULANUpHwHs3VE-awHPfWy3Mu6N4&s=10"></ImgModal>
    </div>

    <div class="container content mt-3">
        <button class="button is-warning" @click="modal3Open = true">Open Modal 3</button>
       <ImgModal :active="modal3Open" @close="modal3Open = false" url="https://picsum.photos/seed/Markus/1280/960/"></ImgModal>
    </div>

</template>

<style></style>