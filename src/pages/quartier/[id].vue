<script setup lang="ts">
    import FormulaireQuartier from "../../components/FormulaireQuartier.vue";
    defineProps<{
      id: string;
    }>();
    </script>
    <template>

    <h1 class="text-2xl font-bold mb-6 mt-3">Modifier le nom du quartier</h1>
      <div class="p-2">
        <FormulaireQuartier :id="id" />
      </div>
    </template>