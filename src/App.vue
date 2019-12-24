<template>
    <v-app>
        <invitePage />
    </v-app>
</template>

<script>
    import invitePage from './components/invitePage.vue';
export default {
  name: 'App',

  components: {
      invitePage,
  },

  data: () => ({
    //
  }),
};
</script>

<style>
    @import url('https://fonts.googleapis.com/css?family=Open+Sans:400,600,700,800&display=swap');
    * {
        font-family: 'Open Sans', sans-serif;
    }
    .theme--light.v-application {
        background-color: #fff !important;
    }
    .menu-container-wrapper .v-expansion-panel::before {
        box-shadow: none !important;
        border: none;
    }
    .menu-container-wrapper .v-expansion-panel:not(:first-child)::after {
        display: none !important;
    }
</style>
