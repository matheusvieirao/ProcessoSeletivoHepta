<template>
  <div>
    <table>
      <tr>
        <th>Nome</th>
        <th>Fabricante</th>
        <th>Volume (mm)</th>
        <th>Unidade</th>
        <th>Estoque</th>
        <th/>
      </tr>
      <tbody v-bind:key="produto_aux.id" v-for="produto_aux in listaprodutos">
        <Produto
          v-bind:produto="produto_aux"
          v-on:del-produto="$emit('del-produto',produto_aux.id)"
        />
      </tbody>
    </table>
  </div>
</template>

<script>
import Produto from "./Produto.vue";
export default {
  name: "ListaProdutos",
  components: {
    Produto
  },
  props: ["listaprodutos"]
};
</script>

<style scoped>
</style>
