<template>
    <div class="p-2">
        <h1 class="text-2xl">Page Simple</h1>
        <card class="w-1/2" v-bind="objet"/>
    </div>
    </template>
    
<script setup lang="ts">
    import card from "../components/card.vue";

    const objet = {nom:"House", prix:500, favori:true, nbrSDB:4,  image:"/image/house.png"}

</script>