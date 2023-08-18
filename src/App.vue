<script setup>
import HeaderMain from './components/header/HeaderMain.vue'
import Welcome from './components/section-welcome/Welcome.vue'
import InputGet from './components/section-checklist/InputGet.vue'

import BodyList from './components/section-checklist/BodyList.vue'
</script>

<template>
  <HeaderMain/>
  <main>
    <Welcome/>
    <InputGet/>
    <BodyList/>
  </main>
</template>

<style scoped>
</style>
