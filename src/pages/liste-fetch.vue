<template>
    <div class="p-5">
        <h1 class="text-2xl">Page Liste fetch</h1>
        <div v-for="maisons in maisons" :key="maisons.nom">
            <card class="w-1/2 mb-10" v-bind="maisons"/>
        </div>
    </div>
</template>

<script setup lang="ts">
    import card from "../components/card.vue";
    const res = await fetch("maisons.json");
    const maisons = await res.json();
</script>