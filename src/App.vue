<template>
  <div class="w-70 h-8 bg-white text-center font-fanwood-text text-[22px]">
  <RouterLink to="Acceuil">
    <p class="ml-2 ">TiK TaK </p>
  </RouterLink>
  </div>
  <div class="flex justify-between w-70 h-8  bg-[#CCBDBE] font-fanwood-text">
    <RouterLink to="/">
      <p class="ml-2 ">PERSONNALISATION </p>
    </RouterLink>
    <RouterLink to="page1produit">
      <p class="">PRODUIT</p>
    </RouterLink>

    <RouterLink to="produits">
      <p class="">PRODUITS</p>
    </RouterLink>

    <RouterLink to="formulaireconnexion">
      <p class="">CONNEXION </p>
    </RouterLink>
  
  </div>
  

  <!-- Affiche les pages -->
  <Suspense>
    <router-view class="" />
  </Suspense>
</template>

<script setup lang="ts">
import { Bars3Icon } from "@heroicons/vue/20/solid";
</script>
