<script setup lang="ts">
    import card from "../components/card.vue";
    import maisons from "../assets/maisons.json"
    defineProps<{ nbr: string }>();
</script>

<template>
    <main>
        <FicheOffreMaison v-bind="maisons[Number(nbr)]" />
    </main>
</template>