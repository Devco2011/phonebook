<template>
  <div>
    <h3>New Contact</h3>
    <v-form @submit.prevent="handleSubmit">
      <v-text-field
        outlined
        label="First Name"
        v-model="form.firstName"
      ></v-text-field>
      <v-text-field
        outlined
        label="Last Name"
        v-model="form.lastName"
      ></v-text-field>
      <v-text-field
        outlined
        type="phone"
        label="Phone"
        v-model="form.phone"
      ></v-text-field>
      <v-select
        outlined
        label="Phone Type"
        :items="options"
        v-model="form.type"
      >
      </v-select>
      <v-text-field outlined label="Email" v-model="form.email"></v-text-field>
      <v-btn type="submit" color="teal" dark>Submit</v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        firstName: "",
        lastName: "",
        phone: "",
        type: "",
        email: "",
      },
      options: ["Home", "Office", "Cell"],
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("contact-submit", this.form);
      this.form = {
        firstName: "",
        lastName: "",
        phone: "",
        type: "",
        email: "",
      };
    },
  },
};
</script>

<style>
</style>