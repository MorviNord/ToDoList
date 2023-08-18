<script setup>
import { ref } from 'vue'
const emit = defineEmits(['close', 'input']);
import { objList } from '../components/section-checklist/baseList';

const closeModal = () => {
  emit('close');
}

const props = defineProps( {
  text: {
    type: String,
    required: true,
  },
})

const value = ref(props.text);

const inputSaveText = () => {
  closeModal();
  emit('input', value.value)
}
</script>

<template>
  <div 
    @click="inputSaveText"
    class="background-modal"
  >
    <div @click.stop class="modal">
        <input type="text" v-model="value" @blur="inputSaveText">
    </div>
  </div>
</template>

<style lang="scss">
@use '../sass/common/vars';

.background-modal {
    position: fixed;

    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
    
    background: rgb(0, 0, 0);
    background-color: #81818150;

    cursor: pointer;
}

.modal {
  position: fixed;
  
  z-index: 10;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  background: vars.$secondary-color;
  border-radius: 0.5rem;

  padding: 2rem
}

</style>