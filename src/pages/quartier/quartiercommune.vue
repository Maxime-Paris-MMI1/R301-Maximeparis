<script setup lang="ts">
    import { supabase } from "../../supabase";
    import groupBy from "lodash/groupBy";
    import {
    Disclosure,
    DisclosureButton,
    DisclosurePanel,
    } from '@headlessui/vue'
    import { ChevronRightIcon } from '@heroicons/vue/20/solid'
    const { data, error } = await supabase.from("allusers").select("*");
    if (error) console.log("n'a pas pu charger la table allusers :", error);
</script>
    
    <template>
      <section class="flex flex-col">
        <h3 class="text-2xl mb-5">Liste des Communes et des quartiers</h3>


        <Disclosure v-for="(listeQuartier, libelleCommune) in groupBy(data,'libelle_Commune')" :key="libelleCommune" v-slot="{ open }">
          <ul>
            <li v-for="quartierObject in listeQuartier">
              <DisclosureButton class="flex justify-start mb-5"> 
                {{ quartierObject.libelle_Commune }}
                <ChevronRightIcon :class="open && 'rotate-90 transform'" class="w-5 h-5" />
              </DisclosureButton> 
            </li>
            <li v-for="quartierObject in listeQuartier" :key="quartierObject.code_Quartier" class="mb-5 font-bold">
              <DisclosurePanel>
                {{ quartierObject.libelle_Quartier }}
              </DisclosurePanel>
            </li>
          </ul>
        </Disclosure>


      </section>
    </template>