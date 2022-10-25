<template>
  <div id="app">
    <div v-if="!clients.length" class="loading">Loading Clients...</div>

    <div class="clients" v-for="client in clients" :key="client.name">
      <h2>{{ client.name }}</h2>
    </div>

    <div v-if="!files.length" class="loading">Loading Files...</div>
    <div class="files" v-for="file in files" :key="file.name">
      <h2>{{ file.name }}</h2>
    </div>
  </div>
</template>

<script>

import axios from 'axios';

export default {
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
      axios.get('http://localhost:3030/files').then((response) => {
        const filesApi = response.data;
        this.files = filesApi;
      }).catch((error) => {
        // eslint-disable-next-line no-console
        console.error(error);
      });
    },

    getClients() {
      axios.get('http://localhost:3030/clients').then((response) => {
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
</style>
