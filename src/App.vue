<script setup>
import ProductDisplay from './components/ProductDisplay.vue';


</script>

<template>
  <header>
    <!-- card position absolute -->
    <!-- <ProductDisplay>

    </ProductDisplay> -->
  </header>

  <main>
    <div class="headtop-container"/>
    <div class="headbottom-container"/>
  </main>
</template>

<style scoped>
    .headtop-container {
        background-image: url('../assets/bg-pattern.svg');

        /* background-color: red; */
        height: 70vh;
    }
    .headbottom-container {
        background-color: #FFFF;
        height: 30vh;
    }
</style>
