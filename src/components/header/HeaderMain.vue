<script setup>
import { ref } from 'vue';
import { menuItems } from './NavigationMenu';

const items = ref(menuItems);

</script>

<template>
  <header>
    <div class="container">
      <div class="header">
        <nav class="menu">
          <ul class="menu-list">
            <li v-for="item in items" 
                :key="item.id" 
                class="menu-list__item"
                >
              <a :href="item.link">
                {{ item.label }}
              </a>
              <span class="menu-list__special" v-if="item.id === 2">Скоро</span>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </header>
</template>

<style lang="scss">
@use '../../sass/common/vars';

header {
  background: vars.$minor-color;

  margin-bottom: 3rem;
}

.menu-list {
  display: flex;

  gap: 0.5rem;

    &__item {
      padding: 1.4rem;

      color: vars.$white-color;
    }

    &__special {
      margin-left: 4px;
      padding: 2px;

      background: vars.$secondary-color--hover;

      border-radius: 4px;
    }

  @media (width < 320px) {
    flex-wrap: wrap;
  }
}

</style>
