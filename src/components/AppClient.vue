<template>

    <div>
      <h2>Name of client: {{ name }}</h2>
      <p>Address: {{ address }}</p>
      <p>Channel: {{ channel }}</p>
    </div>

</template>

<script>
export default {
  props: ['name', 'address', 'channel'],
};
</script>
