<script lang="ts">
    import BotaoPrincipal from './BotaoPrincipal.vue';
    import { obterReceitas } from '@/http/receita';
    import type iReceita from '@/interfaces/iReceita';
    import CardReceita from './CardReceita.vue';

    export default {
        data () {
            return {
                receitas: [] as iReceita[]
            }
        },
        async created() {
            this.receitas = await obterReceitas();
        },
        components: { BotaoPrincipal, CardReceita },
        emits: ['selecionarIngredientes']
    }
</script>
<template>
    <section class="mostra-receitas">
        <h1 class="cabecalho titulo-receitas">Receitas</h1>
        <p v-if="receitas.length > 0" class="paragrafo-lg opcoes">Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!</p>
        <p v-else class="paragrafo-lg opcoes">Ops, não encontramos resultados para sua combinação. Vamos tentar de novo?</p>
        <p class="paragrafo-lg resultados">Resultados encontrados: {{ receitas.length }}</p>

        <ul class="receitas">
            <li v-for="receita in receitas" :key="receita.nome">
                <CardReceita :receita="receita" />
            </li>
        </ul>

        <img v-if="receitas.length === 0" src="../assets/images/sem-receitas.png" alt="Resultado não encontrado!">
    </section>
    <BotaoPrincipal texto="Editar lista"  @click="$emit('selecionarIngredientes')" />
</template>

<style scoped>
    .mostra-receitas {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .titulo-receitas {
        color: var(--verde-medio, #3D6D4A);
        display: block;
        margin-bottom: 1.5rem;
    }

    .opcoes {
        margin-bottom: 2rem;
    }

    .resultados {
        color: var(--verde-medio, #3D6D4A);
        margin-bottom: 2rem;
    }

    .receitas {
        margin-bottom: 1rem;
        display: flex;
        justify-content: center;
        gap: 1.5rem;
        flex-wrap: wrap;
    }
</style>