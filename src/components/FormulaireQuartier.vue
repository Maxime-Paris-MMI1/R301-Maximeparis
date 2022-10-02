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



  <FormKit type="form" :submit-attrs="{ classes: { input: 'bg-indigo-600 px-10 py-2 rounded mt-10 mb-16 hover:motion-safe:animate-pulse text-white' } }" :config="{classes: {input: 'p-1 rounded  border-gray-300 shadow-sm border  hover:bg-gray-200', label: 'text-indigo-800'}}"
    v-model="quartier"  @submit="upsertquartier">
      <FormKit name="libelle_quartier" label="Nom du quartier"/>
      <FormKit name="code_commune" label="Code de la commune"/>
  </FormKit>

</template>
