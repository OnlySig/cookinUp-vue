<script lang="ts">
import SelecionarIngredientes from './SelecionarIngredientes.vue';
import Tag from './Tag.vue';

    const ingredientes = ['FAZ', 'O', 'ÊLÍ']
    
    export default {
        data() {
            return {
                ingredientes
            }
        },
        components: { SelecionarIngredientes, Tag }
    }
</script>

<template>
    <main class="conteudo-principal">
        <section>
            <span class="subtitulo-lg sua-lista-texto">
                Lista de ingredientes
            </span>
            <ul v-if="ingredientes.length" class="ingredientes-sua-lista">
<!-- esse v-if é um if normal e oq ficar na inicialização é a lógica e quando for false esse ul vai sumir -->
<!-- v-for seria um for of q esta pegando os ingredientes no retorno de data no script, no react seria como se fosse um map -->
<!-- v-bind:key é o key no map do react, porem pra vc colocar um elemento js em html nos atributos tem q colocar esse v-bind: antes da propriedade -->
<!-- porem existe uma forma abreviada, ficando assim: :key -->
                <li v-for="ingrediente in ingredientes" :key='ingrediente'>
                    <Tag :ingrediente ativa/>
                </li>
            </ul>
            <!-- esse v-else funfa como else, porem para funcionar tem q estar do lado do v-if -->
            <p v-else class="paragrafo lista-vazia">
                <img src="../assets/images/icones/lista-vazia.svg" alt="icone de lista vazia">
                Sua lista esta vazia, selecione ingredientes para iniciar.
            </p>
        </section>

        <SelecionarIngredientes/>
    </main>
</template>

<style scoped>
    .conteudo-principal {
      padding: 6.5rem 7.5rem;
      border-radius: 3.75rem 3.75rem 0rem 0rem;
      background: var(--creme, #FFFAF3);
      color: var(--cinza, #444);

      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5rem;
    }

    .sua-lista-texto {
      color: var(--coral, #F0633C);
      display: block;
      text-align: center;
      margin-bottom: 1.5rem;
    }

    .ingredientes-sua-lista {
      display: flex;
      justify-content: center;
      gap: 1rem 1.5rem;
      flex-wrap: wrap;
    }


    .lista-vazia {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.25rem;

      color: var(--coral, #F0633C);
      text-align: center;
    }

    @media only screen and (max-width: 1300px) {
      .conteudo-principal {
        padding: 5rem 3.75rem;
        gap: 3.5rem;
      }
    }

    @media only screen and (max-width: 767px) {
      .conteudo-principal {
        padding: 4rem 1.5rem;
        gap: 4rem;
      }
    }
</style>