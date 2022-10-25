<template>

    <app-container>
      <h2>{{ name }}</h2>
      <p>Address: {{ address }}</p>
      <p>Channel: {{ channel }}</p>
    </app-container>

</template>

<script>

import AppContainer from '@/components/AppContainer.vue';

export default {
  components: {
    AppContainer,
  },
  props: {
    name: {
      type: String,
      required: true,
    },
    address: {
      type: String,
      required: true,
    },
    channel: {
      type: Number,
      required: true,
    },
  },
};
</script>
