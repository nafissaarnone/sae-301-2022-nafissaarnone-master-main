<script setup lang="ts">

import type { Montre } from "@/types";
import { ref } from "vue";
import { supabase } from "@/supabase";
import MontreCarré from "./VueMontreCarre.vue";

import {useRouter} from "vue-router";
const router = useRouter();
// @ts-ignore
import FormKitListColors from "./FormKitListColors.vue";

const props = defineProps(["id"]);
const Montres = ref<Montre>({});

if (props.id) {
    let { data, error } = await supabase
        .from("montre")
        .select("*")
        .eq("id_montre", props.id);

    if (error) console.log("n'a pas pu charger le table Montre :", error);
    else Montres.value = (data as any[])[0];
}
// @ts-ignore
async function upsertMontre(dataForm, node) {
    const { data, error } = await supabase.from("montre").upsert(dataForm);
    if (error) node.setErrors([error.message]);
    else {
        node.setErrors([]);
        router.push("/acceuil");
    }
}


</script>



<template>
    <div class="flex bg-[#BFBFBF] gap-x-60">
        <div class="exemple">
            <MontreCarré class="w-montretaille  mt36" v-bind="Montres" id="carré" />
        
        </div>

        <div>
            <FormKit class="envoyer" type="form" v-model="Montres" @submit="upsertMontre" submit-label="ACHETER">
                <div class="selection">
                    <div class="flex gap-4">
                        <FormKitListColors name="boitier1" label="Boitier1" />
                        <FormKit name="boitier1" type="color" />
                    </div>
                    <br>
                    <br>
                    <div class="flex gap-4">
                        <FormKitListColors name="boitier2" label="Boitier2" />
                        <FormKit name="boitier2" type="color" />
                    </div>
                    <br>

                    <div class="flex gap-4">
                        <FormKitListColors name="ecran" label="Ecran" value="#000000" />
                        <FormKit name="ecran" type="color" />
                    </div>
                    <br>
                    <div class="flex gap-4">
                        <FormKitListColors name="bracelet" label="Bracelet" value="#000000" />
                        <FormKit name="bracelet" type="color" />
                    </div>
                    <br>
                    <div class="flex gap-4">
                        <FormKitListColors name="texte" label="texte" />
                        <FormKit name="texte" type="color" />
                    </div>
                </div>
            </FormKit>
        </div>
    </div>
</template>


