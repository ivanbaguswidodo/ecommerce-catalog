<script setup>
import ProductDisplay from './components/ProductDisplay.vue';


</script>

<template>
  <header>
    <!-- card position absolute -->
  </header>

  <main>
    <ProductDisplay>
      <template #headtop>Head Top</template>
      <template #headbottom>Head Bottom</template>
    </ProductDisplay>
  </main>
</template>

<style scoped>
</style>
