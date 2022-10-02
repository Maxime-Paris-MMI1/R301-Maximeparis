<script setup lang="ts">
  import { supabase } from "@/supabase";
  import { ref } from "@vue/reactivity";

  const quartier = ref({ });

    
    import { useRouter } from "vue-router";
    const router = useRouter();
    const props = defineProps(["code_commune"]);
    if (props.code_commune) {
     // On charge les données du quartier
     let { data, error } = await supabase
     .from("quartier")
     .select("*")
     .eq("code_commune", props.code_commune);
     if (error) console.log("n'a pas pu charger le table quartier :", error);
     else quartier.value = (data as any[])[0];
    }

    async function upsertquartier(dataForm, node) {
    const { data, error } = await supabase.from("quartier").upsert(dataForm);
    if (error) node.setErrors([error.message])
    else {
    node.setErrors([]);
    router.push({ name: "quartier-id", params: { id: data[0].id } });
    }
  }

</script>


<template>

  <h1 class="text-2xl font-bold mb-6">Modifier le nom du quartier</h1>

  <FormKit type="form" 
    v-model="quartier"  @submit="upsertquartier">
      <FormKit name="libelle_quartier" label="Nom du quartier"/>
      <FormKit name="code_commune" label="Code de la commune"/>
  </FormKit>

</template>
