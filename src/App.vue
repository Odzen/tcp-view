<template>
  <div id="app">

    <div class="container" v-for="client in clients" :key="client.name">
       <p v-if="!clients.length" class="loading">Loading Clients...</p>
      <app-client :name="client.name" :address="client.address" :channel="client.channel" />
    </div>

    <!-- <div  v-for="file in files" :key="file.name">
      <p v-if="!files.length" class="loading">Loading Files...</p>
      <h2>{{ file.name }}</h2>
    </div> -->

  </div>
</template>

<script>

import axios from 'axios';
import AppClient from '@/components/AppClient.vue';

export default {
  components: {
    AppClient,
  },

  data() {
    return {
      bottom: false,
      clients: [],
      files: [],
    };
  },

  watch: {
    files() {
      setTimeout(() => {
        this.getFiles();
      }, 2000);
    },

    clients() {
      setTimeout(() => {
        this.getClients();
      }, 2000);
    },
  },
  created() {
    this.getFiles();
    this.getClients();
  },

  methods: {

    getFiles() {
      axios.get(`http://${process.env.VUE_APP_HOST_BACKEND}:${process.env.VUE_APP_PORT_BACKEND}/files`).then((response) => {
        const filesApi = response.data;
        this.files = filesApi;
      }).catch((error) => {
        // eslint-disable-next-line no-console
        console.error(error);
      });
    },

    getClients() {
      axios.get(`http://${process.env.VUE_APP_HOST_BACKEND}:${process.env.VUE_APP_PORT_BACKEND}/clients`).then((response) => {
        const clientsApi = response.data;
        this.clients = clientsApi;
      }).catch((error) => {
        // eslint-disable-next-line no-console
        console.error(error);
      });
    },
  },
};
</script>

<style lang="scss">
  body {
    font-family: 'Archivo Narrow', sans-serif;
    background: #1f2d30;
  }
  .display {
    display: flex;
    justify-content: center;
    align-content: center;
  }

  #app {
    @extend .display;
    flex-direction: column;
  }
</style>
