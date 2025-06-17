<script lang="ts">
    import type { PropType } from 'vue';
    import type iReceita from '@/interfaces/iReceita';

    export default {
        props: {
            receita: {type: Object as PropType<iReceita>, required: true}
        },
    }
</script>

<template>
    <article class="card-receita">
        <img class="imagem-receita" :src="`/imagens/receitas/${ receita.imagem }`" :alt="`Receita: ${ receita.nome }`">
        <p class="paragrafo-receita">{{ receita.nome }}</p>
    </article>
</template>

<style scoped>
    .card-receita {
        width: 19.5rem;
        border-radius: 1rem;
        background: var(--branco, #FFF);
        box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .imagem-receita {
        border-radius: 16px 16px 0 0;
        width: 100%;
    }

    .paragrafo-receita {
        padding: 1.6rem 0;
    }
</style>
