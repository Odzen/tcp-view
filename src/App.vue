<template>
  <div id="app">
    <h1> Welcome to the TCP Server 🌐</h1>

      <h2 class="h2-title"> Clients {{clients.length}}</h2>
      <p v-if="!clients.length" class="loading">Loading Clients...</p>
      <div  v-for="client, index  in clients" :key="index">
        <app-client :name="client.name" :address="client.address" :channel="client.channel" />
      </div>

      <h2 class="h2-title"> Files {{files.length}}</h2>
      <p v-if="!files.length" class="loading">Loading Files...</p>
      <div  v-for="file, index in files" :key="index">
        <app-file
          :name="file.name"
          :size="file.size"
          :content="file.content"
          :address="file.address"
          :pipeline="file.pipeline"
      />
    </div>

  </div>
</template>

<script>

import axios from 'axios';
import AppClient from '@/components/AppClient.vue';
import AppFile from '@/components/AppFile.vue';

export default {
  components: {
    AppClient,
    AppFile,
  },

  data() {
    return {
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
    background: #8aacb4;
  }

  h1 {
    margin-top: 40px;
    color: rgb(0, 0, 0);
    text-align: center;
  }

  .h2-title{
    font-size: 30px;
    color: rgb(0, 0, 0);
    text-align: center;
  }

  .loading {
  color: white;
  text-align: center;
  font-size: 20px;
  }

  .display {
    display: flex;
    justify-content: center;
    align-content: center;
    text-align: center;
  }

  #app {
    @extend .display;
    flex-direction: column;

  }

</style>
