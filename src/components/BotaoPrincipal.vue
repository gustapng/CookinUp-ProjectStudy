<script lang="ts">
    export default {
        props: {
            texto: { type: String, required: true }
        }
    }
</script>

<template>
    <button class="botao-editar">
        {{ texto }}
    </button>
</template>

<style scoped>
    .botao-editar {
        color: var(--creme, #FFFAF3);
        background-color: #F0633C;
        text-align: center;
        width: 312px;
        height: 56px;
        border-radius: 32px;
        font-weight: 700;
        cursor: pointer;
    }
</style>
