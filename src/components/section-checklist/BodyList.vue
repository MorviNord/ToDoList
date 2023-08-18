<script setup>
import { ref, computed } from 'vue';
import ToDoItem from './ToDoItem.vue';
import { objList } from './baseList';

const objListItems = ref(objList);

const isShowBody = computed(() => objListItems.value.length > 0);

const removeItemList = (i) => {
  objListItems.value.splice(i, 1);
}

const updateText = (todoToUpdate) => {
  objList.value = objList.value.map((item) => item.id === todoToUpdate.id ? todoToUpdate : item)
};

</script>

<template>
  <section v-if="isShowBody" class="body">
    <div class="container">
      <div class="body-header">
        <h2 class="body-header__title">
          Список дел
        </h2>
      </div>
      <div class="body-list">
        <ToDoItem
          v-for="item of objListItems"
          :key="item.id"
          :id="item.id"
          :text="item.text"
          :isDone="item.isDone"
          v-model:is-done="item.isDone"
          @on-delete-click="removeItemList"
          @update:isDone="updateText"
          @updateText="updateText"
        />
      </div>
    </div>
  </section>
</template>

<style lang="scss">
@use '../../sass/common/vars';

.body-header {
    margin-bottom: 2rem;

        &__title {
            color: vars.$white-color;
        }
}

.check {
  display: flex;
  align-items: center;
  gap: 1rem;

  &__input {
    position: absolute;
    appearance: none;

    &:checked + .check__box::after {
      content: "";
      background: url(../../img/svg/check.svg);
      background-position: center;
      background-repeat: no-repeat;
      width: 100%;
      height: 100%;
    }
  }

  &__box {
    display: flex;
    position: relative;
    width: 24px;
    height: 24px;
    border-radius: 6px;
    border: 2px solid vars.$secondary-color;
  }

  &:has(.check__input:checked) {
    p {
      text-decoration: line-through;
    }
  }
}


</style>