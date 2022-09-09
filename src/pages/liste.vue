<template>
    <div class="p-4">
        <h1 class="text-2xl"> Page Liste</h1>
        <div v-for="maisons in maisons" :key="maisons.nom">
            <card class="w-1/2 mb-10" v-bind="maisons"/>
        </div>
    </div>
</template>

<script setup lang="ts">
    import card from "../components/card.vue";

  const maisons = [{nom:"Maison1", prix:589, nbrSDB:5, image:"/image/house.png", favori:true,}
  , {nom:"Maison2", prix:739, nbrSDB:2, image:"/image/house2.png", favori:false,}
  , {nom:"Maison3", prix:350, nbrSDB:4, image:"/image/house3.jpg", favori:true,}]
</script>