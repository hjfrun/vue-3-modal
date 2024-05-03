<script setup>
  import { ref } from 'vue'
  import { onClickOutside } from '@vueuse/core'

  const isModalOpen = ref(false)
  const modal = ref(null)
  onClickOutside(modal, () => {
    isModalOpen.value = false
  })
</script>

<template>
  <h1>🔥 Vue 3 Modal!</h1>
  <button class="open-btn" @click="isModalOpen = true">Open Modal</button>
  <Teleport to="#modal">
    <Transition name="modal">
      <div class="modal-bg" v-if="isModalOpen">
        <div class="modal" ref="modal">
          <button class="close-btn" @click="isModalOpen = false">X</button>
          Click outside to close this modal to close it
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<style scoped>
  h1 {
    text-align: center;
  }

  /** center the open modal button */
  .open-btn {
    display: block;
    margin-left: auto;
    margin-right: auto;
  }

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

  .modal-enter-active,
  .modal-leave-active {
    transition: all 0.25s ease;
  }

  .modal-enter-from,
  .modal-leave-to {
    opacity: 0;
    transform: scale(1.1);
  }

  html {
    background: #ecf0f1;
  }
</style>
