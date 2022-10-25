<template>

    <app-container>
      <h2>{{ name }}</h2>
      <p>Size: {{ size }}</p>
      <p>Content: {{ content }}</p>
      <p>Address: {{ address }}</p>
      <p>Pipeline: {{ pipeline }}</p>
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
    size: {
      type: Number,
      required: true,
    },
    content: {
      type: String,
      required: true,
    },
    address: {
      type: String,
      required: true,
    },
    pipeline: {
      type: Number,
      required: true,
    },
  },
};
</script>
