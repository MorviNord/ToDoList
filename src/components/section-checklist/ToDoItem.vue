<script setup>
import { ref } from 'vue';
import UInputModal from '@/UI/UInputModal.vue';

const isShowModal = ref(false);

let func = () => {
    console.log()
    isShowModal.value = true;
}

const inputSaveText = () => {
  emit('updateText', { text: text, id: props.id, isDone: props.isDone });
  closeModal();
};

const emit = defineEmits(['onCheckboxChange', 'onDeleteClick', 'onEditClick', 'update:isDone', 'updateText']);

const props = defineProps({
  text: {
    type: String,
    required: true
  },
  id: {
    type: Number,
    required: true
  },
  isDone: {
    type: Boolean,
    required: true
  },
});

</script>
<template>
    <div 
        class="body-list__item"
        >
        <div class="paragraph">
            <label class="check">
                <input
                    class="check__input"
                    type="checkbox"
                    @change="$emit('update:isDone', { text: text, id: props.id, isDone: !props.isDone })"
                />
                <span class="check__box"></span>
                <p>{{ text }}</p>
            </label>
        </div>
        <div class="body-list__item-col">
            <button @click="func" class="body-list__item-col--edit">
                <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0.771262 14C0.555767 13.9996 0.350338 13.9087 0.205094 13.7495C0.0571725 13.5916 -0.0163304 13.378 0.00305578 13.1624L0.191266 11.0923L8.88583 2.39845L11.603 5.11557L2.91072 13.8087L0.841169 13.9969C0.817355 13.9992 0.79354 14 0.771262 14ZM12.1453 4.5723L9.42895 1.85518L11.0583 0.225366C11.2024 0.0810753 11.3979 0 11.6018 0C11.8057 0 12.0012 0.0810753 12.1453 0.225366L13.7747 1.85518C13.9189 1.99931 14 2.19489 14 2.39883C14 2.60278 13.9189 2.79836 13.7747 2.94249L12.1461 4.57153L12.1453 4.5723Z"/>
                </svg>
            </button>
            <button 
                    class="body-list__item-col--close" 
                    @click="$emit('onDeleteClick', {id, text, isDone})">
                <svg
                    width="16" 
                    height="16" 
                    viewBox="0 0 24 24" 
                    fill="none" 
                    xmlns="http://www.w3.org/2000/svg"
                    >
                    <path d="M23.2971 4.09704C24.2343 3.15978 24.2343 1.6402 23.2971 0.702933C22.3599 -0.234311 20.8402 -0.234311 19.903 0.702933L12.0001 8.60588L4.09713 0.702933C3.15986 -0.234311 1.64028 -0.234311 0.703008 0.702933C-0.23424 1.6402 -0.23424 3.15978 0.703008 4.09704L8.60599 11.9999L0.702936 19.9029C-0.234312 20.8401 -0.234312 22.3597 0.702936 23.2969C1.64021 24.2344 3.15979 24.2344 4.09706 23.2969L12.0001 15.394L19.903 23.2969C20.8402 24.2341 22.3599 24.2341 23.2971 23.2969C24.2343 22.3597 24.2343 20.8401 23.2971 19.9029L15.3941 11.9999L23.2971 4.09704Z"/>
                </svg>
            </button>
        </div>
    </div>
    <UInputModal 
        v-if="isShowModal"
        :text="text"
        @close="isShowModal = false"
        @input="text = $event"
        
        @onInput="inputSaveText"
    />
</template>

<style lang="scss">
@use '../../sass/common/vars';

.body-list {
    display: flex;
    flex-direction: column;
    width: 100%;

    padding: 1rem;

    border-radius: 0.5rem;
    background: vars.$minor-color--3;

        .paragraph {
            display: flex;
            align-items: center;
            
            gap: 1rem;
        }

        &__item {
            display: flex;
            justify-content: space-between;

            padding: 1rem;

            border-bottom: 2px solid vars.$primary-color;

            white-space: normal;
            color: vars.$white-color;

            &:last-child {
                border-bottom: none;
            }

                &-col {
                    display: flex;
                    align-items: center;

                    gap: 0.5rem;

                    &--edit {
                        display: flex;

                        padding: 4px;

                        border: 1px solid vars.$text-secondary;
                        border-radius: 6px;

                        background: none;
                        cursor: pointer;

                            svg {
                                fill: vars.$orange-color;
                            }
                    }


                    &--close {
                        display: flex;

                        border: none;

                        background: none;
                        cursor: pointer;

                            svg {
                            fill: vars.$text-secondary;
                            }
                    }
                }
        }
}
</style>