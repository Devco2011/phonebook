<template>
  <div>
    <contacts-table :contacts="contacts" />
    <contact-form @contact-submit="addContact" />
  </div>
</template>

<script>
import ContactForm from "./ContactForm";
import ContactsTable from "./ContactsTable";

export default {
  components: { ContactForm, ContactsTable },
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