<template>
  <contact-form @contact-submit="addContact" />
</template>

<script>
import ContactForm from "./ContactForm";
export default {
  components: { ContactForm },
  data() {
    return {
      contacts: [],
    };
  },
  methods: {
    addContact(contact) {
      this.contacts.push(contact);
    },
  },
};
</script>

<style>
</style>