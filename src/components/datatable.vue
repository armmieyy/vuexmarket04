<template>
  <div>
    <v-row no-gutters>
      <v-col md="1"><v-card class="pa-2 blue lighten-2" outlined> ID</v-card></v-col>
      <v-col md="2"><v-card class="pa-2 blue lighten-2" outlined> User name</v-card></v-col>
      <v-col md="2"><v-card class="pa-2 blue lighten-2" outlined> Password</v-card></v-col>
      <v-col md="2"><v-card class="pa-2 blue lighten-2" outlined> Phonenumber</v-card></v-col>
      <v-col md="3"><v-card class="pa-2 blue lighten-2" outlined> Email address</v-card></v-col>
      <v-col md="1"><v-card class="pa-2 blue lighten-2" outlined> Gender</v-card></v-col>
    </v-row>
    <v-row v-for="(items, index) in $store.getters.items" :key="index"  no-gutters>
      <v-col md="1"><v-card class="pa-2" outlined> {{ index + 1 }}</v-card></v-col>
      <v-col md="2"><v-card class="pa-2" outlined> {{ items.name }}</v-card></v-col>
      <v-col md="2"><v-card class="pa-2" outlined> {{ items.pass }}</v-card></v-col>
      <v-col md="2"><v-card class="pa-2" outlined> {{ items.Phonenumber }}</v-card></v-col>
      <v-col md="3"><v-card class="pa-2" outlined> {{ items.email }}</v-card></v-col>
      <v-col md="1"><v-card class="pa-2" outlined> {{ items.select }}</v-card></v-col>
      <td></td>
    </v-row>
    <v-btn class="mr-4" @click="page">Register more</v-btn>
  </div>
</template>
<script>
export default {
  methods: {
    page() {
      this.$store.state.page = 1;
    },
  },
};
</script>
<style>
</style>