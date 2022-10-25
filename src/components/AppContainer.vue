<template>

    <div class="container">
        <slot class="slot"></slot>
    </div>

</template>

<style lang="scss" scoped>
    .display {
        display: flex;
        justify-content: center;
        align-content: center;
    }

    .container {
        @extend .display;
        flex-direction: column;
        background: #1c1850;
        width: auto;
        margin: 20px auto;
        box-shadow: 0 2px 3px 1px rgba(30, 0, 0, 0.1);
        color: white;
        word-wrap: break-word;
        padding: 20px;
        font-family: 'Contrail One', sans-serif;
        border-radius: 15px;

    }

</style>
