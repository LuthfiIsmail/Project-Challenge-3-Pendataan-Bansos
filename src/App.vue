<template>
  <v-app>
    <v-app-bar
      color="primary"
      dark
    >
      <v-icon class="pa-4">mdi-pencil</v-icon>
      <v-toolbar-title color="primary">
        Input Pendataan Bansos
      </v-toolbar-title>
    </v-app-bar>

    <v-main>
      <Form></Form>
    </v-main>
  </v-app>
</template>

<script>
import Form from './components/Form.vue';

export default {
  components: {
    Form,
  },
};
</script>
