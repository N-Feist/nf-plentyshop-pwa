<template>
  <UiFormLabel>
    Validate VAT Number?
  </UiFormLabel>
  <SfSelect v-model="selectedVatNumberValidation" data-testid="editor-vat-number-validation-select">
    <option
      v-for="vatNumberOption in vatNumberSettingsOptions"
      :key="vatNumberOption.key"
      :value="vatNumberOption.key"
      class="font-medium text-sm md:text-base"
    >
      {{ vatNumberOption.text }}
    </option>
  </SfSelect>
</template>

<script setup lang="ts">
import { SfSelect } from '@storefront-ui/vue';
const { updateSetting, getSetting } = useSiteSettings('vatNumberValidation');


const vatNumberSettingsOptions = ref([
  {
    key: '0',
    text: 'Yes',
  },
  {
    key: '1',
    text: 'No',
  }
]);

const selectedVatNumberValidation = computed({
  get: () => getSetting(),
  set: (value) => updateSetting(value),
});
</script>
