<script setup>
import { ref } from 'vue';

const props = defineProps(['contacts', 'filteredContacts']);
const emit = defineEmits(['search']);
const form = ref('');

const handleSearch = () => {
  const queryResults = props.contacts.filter((i) => i.firstName.toLowerCase().includes(form.value.toLowerCase()))
  emit('search', queryResults, form.value)
}

</script>

<template>
  <form>
    <div class="is-flex is-flex-direction-row">
      <label class="label">Search</label>
      <input @input="handleSearch" v-model="form" type="text">
    </div>
  </form>
</template>

<style scoped></style>
