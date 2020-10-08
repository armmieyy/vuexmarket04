<template>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="name"
      :counter="10"
      :rules="nameRules"
      label="User name"
      required
    ></v-text-field>
    <v-text-field
      v-model="password"
      :counter="10"
      :rules="passRules"
      label="Password"
      required
    ></v-text-field>
    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>
    <v-text-field
      v-model="Phonenumber"
      :counter="10"
      :rules="passRules"
      label="Phonenumber"
      required
    ></v-text-field>
    <v-select
      v-model="select"
      :items="items"
      :rules="[v => !!v || 'Item is required']"
      label="เพศ"
      required
    ></v-select>
    <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || 'You must agree to continue!']"
      label="Do you agree?"
      required
    ></v-checkbox>
    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="validate"
    >
      Validate
    </v-btn>
    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Reset Form
    </v-btn>
  </v-form>
</template>
<script>
  export default {
    data: () => ({
      valid: true,
      name: '',
      password: '',
      nameRules: [
        v => !!v || 'User name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
       passRules: [
        v => !!v || 'Password is required',
        v => (v && v.length <= 10) || 'Password must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      Phonenumber: '',
      select: null,
      items: [
        'ชาย',
        'หญิง',
      ],
      checkbox: false,
    }),
    methods: {
      validate () {
        if (this.name) {
        let payload = {
          name: this.name,
          pass: this.password,
          email: this.email,
          Phonenumber: this.Phonenumber,
          select: this.select
        };
        this.$store.dispatch("setItem", payload);
        this.$store.state.page = 2;
      }  
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
    },
  }
</script>
<style>
</style>