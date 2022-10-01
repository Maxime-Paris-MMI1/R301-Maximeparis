<script setup lang="ts">
    import { supabase } from "../../supabase";
    import groupBy from "lodash/groupBy";
    import {
    Disclosure,
    DisclosureButton,
    DisclosurePanel,
    } from '@headlessui/vue'
    const { data, error } = await supabase.from("allusers").select("*");
    if (error) console.log("n'a pas pu charger la table allusers :", error);
</script>
    
    <template>
      <section class="flex flex-col">
        <h3 class="text-2xl">Liste des quartiers</h3>

        
        <ul>
          <li v-for="quartierObject in (data as any[])">
            {{ quartierObject.libelle_Commune }} -
            {{ quartierObject.libelle_Quartier }}
          </li>
        </ul>

        
        <Disclosure v-for="(listeQuartier, libelleCommune) in groupBy(data,'libelle_Commune')" :key="libelleCommune">
          <DisclosureButton> </DisclosureButton>
        </Disclosure>


        <Disclosure>
          <DisclosurePanel>
            <ul>
              <li
              v-for="quartierObject in listeQuartier"
              :key="quartierObject.code_Quartier"
              >
              </li>
            </ul>
          </DisclosurePanel>

        </Disclosure>


      </section>
    </template>