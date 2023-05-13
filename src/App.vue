<script setup>
import ProductDisplay from './components/ProductDisplay.vue';


</script>

<template>
  <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@500&family=Poppins:wght@400;500;700&display=swap" rel="stylesheet">
  <header>
    <!-- card position absolute -->
    <ProductDisplay>

    </ProductDisplay>
  </header>

  <main>
    
  </main>
  <div class="headtop-container"/>
  <div class="headbottom-container"/>
</template>

<style scoped>

    .headtop-container {
        background-image: url('./assets/bg-pattern.svg');
        height: 70vh;
    }
    .headbottom-container {
        background-color: #FFFF;
        height: 30vh;
    }


</style>
