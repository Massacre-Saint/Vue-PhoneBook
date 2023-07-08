<script setup>
import { ref } from 'vue';
import ContactForm from './components/ContactForm.vue'
import ContactList from './components/ContactList.vue'
import sampleData from './sampleData';

const contacts = ref(sampleData)
const filteredContacts = ref(contacts.value)
const addContact = (contact) => {
  contacts.value = [...contacts.value, contact]
}

const deleteContact = (contact,) => {
  contacts.value = contacts.value.filter((i) => i.phoneNumber != contact.phoneNumber)
}

const handleQuery = (array, input) => {
  if (input.length > 0) {
    filteredContacts.value = array
  } else filteredContacts.value = contacts.value
}
</script>

<template>
 <h1 class="is-size-1 has-text-centered has-text-info">Vue Phonebook</h1>
 <div class="container px4">
    <div class="columns">
      <div class="column">
        <ContactForm @submit="addContact"/>
      </div>
      <div class="column">
        <ContactList
        @search="handleQuery"
        @delete="deleteContact"
        :filteredContacts="filteredContacts"
        :contacts="contacts"/>
      </div>
    </div>
 </div>
</template>

<style scoped>

</style>
