<script setup lang="ts">

    import { ref } from "@vue/reactivity";
    
    import Card from "./card.vue";
    // On fait une variable réactive qui réference les données
    // ATTENTION : faire une Ref pas une Reactive car :
    // c'est l'objet qui doit être réactif, pas ses props
    const maison = ref({ prix:0, nom:"Nom de la maison",  nbrSDB:0, nbrChambres:0, image:"/image/house.png", favori:false});


    import { useRouter } from "vue-router";
    const router = useRouter();
    const props = defineProps(["id"]);
    if (props.id) {
     // On charge les données de la maison
     let { data, error } = await supabase
     .from("Maison")
     .select("*")
     .eq("id", props.id);
     if (error) console.log("n'a pas pu charger le table Maison :", error);
     else maison.value = (data as any[])[0];
    }
    async function upsertMaison(dataForm, node) {
    const { data, error } = await supabase.from("Maison").upsert(dataForm);
    if (error) node.setErrors([error.message])
    else {
    node.setErrors([]);
    router.push({ name: "edit-id", params: { id: data[0].id } });
    }
}
</script>
<template>
    <div>
        <div class="p-2">
            <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
            <!-- Optionnel on affiche les données -->
            <Card v-bind="maison" />
        </div>
     <div class="p-2 text-center">
        <!-- On passe la "ref" à FormKit -->
        <FormKit type="form" :submit-attrs="{ classes: { input: 'bg-indigo-600 px-10 py-2 rounded mt-10 mb-16 hover:motion-safe:animate-pulse text-white' } }" :config="{classes: {input: 'p-1 rounded  border-gray-300 shadow-sm border  hover:bg-gray-200', label: 'text-indigo-800'}}" 
        v-model="maison" @submit="upsertMaison" >
            <FormKit name="nom" label="Nom"  />
            <FormKit name="prix" label="Prix" type="number" />
            <FormKit name="nbrSDB" label="Nombre de salle de bain" type="number" />
            <FormKit name="nbrChambres" label="Nombre de chambres" type="number" />
            <div class="flex justify-center">
                <FormKit name="favori" label="Àjouter aux favoris"
                type="checkbox"  wrapper-class="flex" :submit-attrs="{ classes: { input: 'bg-red-300 p-1 rounded' } }"/>
            </div>
        </FormKit>
     </div>
    </div>
</template>