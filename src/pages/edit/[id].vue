<script setup lang="ts">
    import Formulaire from '../../components/FormulaireOffreMaison.vue'
    defineProps(["id"]);
    </script>
    
<template>
    <Formulaire :id="id" />
</template>