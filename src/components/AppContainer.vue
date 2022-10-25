<template>

    <div>
        <slot></slot>
    </div>

</template>

<style lang="scss" scoped>
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
