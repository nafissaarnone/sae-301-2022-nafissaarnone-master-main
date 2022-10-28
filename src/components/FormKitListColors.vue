<script setup lang="ts">
import { colors } from "@/types";
defineProps<{
    name: string,
    label: string,
}>();

</script>
<template>
    <div class="bg- rounded-lg">
    <FormKit :name="name" :label="label" value="#FFFFFF" type="radio" :options="colors" :sections-schema="{
        inner: { $el: null },
        decorator: { $el: null },
    }" input-class="peer sr-only" options-class="grid grid-cols-5 gap-5">
        <template #label="context">
            <div class="h-5 w-5 rounded-full border-2 peer-checked:border-red-600 hover:scale-125 transition duration-500"
                :style="{ backgroundColor: context.option.value }"></div>
            <span class="sr-only">{{ context.option.label }}</span>
        </template>
    </FormKit>
    </div>
</template>