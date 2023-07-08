<script setup>
import ContactListItem from './ContactListItem.vue';
import SearchBar from './SearchBar.vue';

const props = defineProps(['contacts','filteredContacts'])
const emit = defineEmits(['delete', 'search']);

const handleQuery = (array, input) => {
  emit('search', array, input)
}
</script>

<template>
  <div class="panel is-success">
    <div class="panel-heading">
      Contacts
    </div>
    <div>
      <SearchBar
      @search="handleQuery"
      :filteredContacts="filteredContacts"
      :contacts="contacts"/>
    </div>
    <div class="panesl-block is-flex is-flex-direction-column is-align-items-stretch">
      <div v-for="contact in props.filteredContacts"
        :key="contact.phoneNumber">
        <ContactListItem @delete="emit('delete', contact)" :contact="contact"/>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
