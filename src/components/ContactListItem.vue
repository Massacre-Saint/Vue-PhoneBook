<script setup>
import { computed } from 'vue';

const props = defineProps(['contact']);
const emit = defineEmits(['delete']);

const initials = computed(() => {
  const firstI = props.contact.firstName[0];
  const lastI = props.contact.lastName[0];
  return firstI + lastI;
})

const fullName = computed(() => {
  return `${props.contact.firstName} ${props.contact.lastName}`
})

</script>

<template>
  <div class="is-flex is-align-items-center py-1">
    <div class="has-background-info has-text-light mr-3 initials">
      <div class="has-text-weight-bold">{{ initials }}</div>
    </div>
    <div class="is-flex-grow-1">
      <p class="is-size-5">
        {{ fullName }}
      </p>
      <div class="is-size-7 has-text-grey">
        <span class="has-text-weight-semibold">Email:</span> {{ props.contact.email }}
      </div>
      <div class="is-size-7 has-text-grey">
        <span class="has-text-weight-semibold">Phone:</span> {{ props.contact.phoneNumber }}
      </div>
    </div>
    <button @click="emit('delete')" class="button is-danger is-light is-small">Remove</button>
  </div>
</template>

<style scoped>
.initials {
  border-radius: 50%;
  width: 3rem;
  height: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
