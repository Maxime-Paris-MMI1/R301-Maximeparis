<script setup lang="ts">
  import ListSupabaseVue from "@/pages/List-Supabase.vue";
import quartiercommuneVue from "@/pages/quartier/quartiercommune.vue";
import { supabase } from "@/supabase";
  import { ref } from "@vue/reactivity";



    
    import { useRouter } from "vue-router";
    const router = useRouter();
    const props = defineProps(["code_commune", "code_Quartier"]);
    if (props.code_commune) {
     // On charge les données du Quartier
     let { data, error } = await supabase
     .from("Quartier")
     .select("*")
     .eq("code_commune", props.code_commune);
     if (error) console.log("n'a pas pu charger le table Quartier :", error);
     else Quartier.value = (data as any[])[0];
    }

    async function upsertQuartier(dataForm, node) {
    const { data, error } = await supabase.from("Quartier").upsert(dataForm);
    if (error) node.setErrors([error.message])
    else {
    node.setErrors([]);
    router.push({ name: "/quartier/quartiercommune", params: { id: data[0].id } });
    }
  }
  let { data } = await supabase
  const Quartier = ref ({ code_commune: "NUL", code_Quartier:"NUL"});
  

</script>


<template>



  <FormKit type="form"  :submit-attrs="{ classes: { input: 'bg-indigo-600 px-10 py-2 rounded mt-10 mb-16 hover:motion-safe:animate-pulse text-white' } }" :config="{classes: {input: 'p-1 rounded  border-gray-300 shadow-sm border  hover:bg-gray-200', label: 'text-indigo-800'}}"
    v-model="Quartier"  @submit="upsertQuartier">
      <FormKit name="libelle_Quartier" label="Nom du Quartier"/>
      <FormKit name="code_commune" label="Code de la commune"/>
      <FormKit name="code_Quartier" label="Code du Quartier"/>
  </FormKit>


<!-- Affiche les communes avec comme valeur l'id de la relation -->
<FormKit
        type="select"
        name="code_Commune"
        label="Commune"
      />
</template>
