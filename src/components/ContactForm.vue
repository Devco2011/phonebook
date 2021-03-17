<template>
  <div>
    <h3>New Contact</h3>
    <v-form @submit.prevent="handleSubmit" ref="contactForm">
      <v-text-field
        outlined
        label="First Name"
        v-model="form.firstName"
        :rules="validators.firstName"
      ></v-text-field>
      <v-text-field
        outlined
        label="Last Name"
        v-model="form.lastName"
        :rules="validators.lastName"
      ></v-text-field>
      <v-text-field
        outlined
        type="phone"
        label="Phone"
        v-model="form.phone"
        :rules="validators.phone"
      ></v-text-field>
      <v-select
        outlined
        label="Phone Type"
        :items="options"
        v-model="form.type"
      >
      </v-select>
      <v-text-field
        outlined
        label="Email"
        v-model="form.email"
        :rules="validators.email"
      ></v-text-field>
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
      validators: {
        firstName: [
          (val) => !!val || "First name is required",
          (val) => val.length < 25 || "Name must be less than 25 characters",
        ],
        lastName: [
          (val) => !!val || "Last name is required",
          (val) =>
            val.length < 25 || "Last name must be less than 25 characters",
        ],
        phone: [
          (val) => !!val || "Phone number is required",
          (val) => val.length === 10 || "Not a valid phone number",
        ],
        email: [
          (val) => !!val || "Email is required",
          (val) => val.includes("@") || "Email must include @",
        ],
      },
    };
  },
  methods: {
    handleSubmit() {
      // check validity
      const isValid = this.$refs.contactForm.validate();

      if (!isValid) {
        return;
      }
      this.$emit("contact-submit", this.form);
      this.form = {
        firstName: "",
        lastName: "",
        phone: "",
        type: "",
        email: "",
      };

      this.$refs.contactForm.resetValidation();
    },
  },
};
</script>

<style>
</style>