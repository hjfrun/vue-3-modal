<script setup>
  import { ref } from 'vue'

  const isModalOpen = ref(false)
</script>

<template>
  <h1>🔥 Vue 3 Modal!</h1>
  <button @click="isModalOpen = true">Open Modal</button>
  <Teleport to="#modal">
    <div class="modal-bg" v-if="isModalOpen">
      <div class="modal">
        <button class="close-btn" @click="isModalOpen = false">X</button>
        Click outside to close this modal to close it
      </div>
    </div>
  </Teleport>
</template>

<style scoped>
  .modal-bg {
    /* always show the modal in the center of the screen */
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;

    /** Darken the screen */
    background-color: rgba(0, 0, 0, 0.5);

    /** center the modal itself */
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    /** need to position button */
    position: relative;

    /** these are all just for aesthetic purposes */
    background: white;
    padding: 50px 100px;
    border-radius: 5px;
    box-shadow: 0px 10px 5px 2px rgba(0, 0, 0, 0.1);
  }

  .modal .close-btn {
    /** put our button in the top right */
    position: absolute;
    top: 10px;
    right: 10px;

    /** remove some of the default button styling */
    background: none;
    border: none;
    cursor: pointer;
  }
</style>
