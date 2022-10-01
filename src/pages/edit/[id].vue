<script setup lang="ts">
    import Formulaire from '../../components/FormulaireOffreMaison.vue'
    defineProps(["id"]);
    </script>
    
<template>
    <div class="flex justify-center w-11/12">
        <Formulaire :id="id" />
    </div>
</template>