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
      <tr>
        <th>
          <input type="text" v-model="prod.nome" name="nome" placeholder="Nome...">
        </th>
        <th>
          <input
            type="text"
            v-model="prod.fabricante"
            name="fabricante"
            placeholder="Fabricante..."
          >
        </th>
        <th>
          <input type="text" v-model="prod.volume.altura" name="altura" placeholder="Altura...">
          <input type="text" v-model="prod.volume.largura" name="largura" placeholder="Largura...">
          <input
            type="text"
            v-model="prod.volume.profundidade"
            name="profundidade"
            placeholder="Profundidade..."
          >
        </th>
        <th>
          <input type="text" v-model="prod.unidade" name="unidade" placeholder="Unidade...">
        </th>
        <th>
          <input type="text" v-model="prod.estoque" name="estoque" placeholder="Estoque...">
        </th>
        <th>
          <input type="submit" value="Submit" class="btn" @click.prevent.stop="addProduto">
        </th>
      </tr>
    </table>
  </div>
</template>

<script>
import Produto from "./Produto.vue";
import uuid from "uuid";

export default {
  name: "ListaProdutos",
  components: {
    Produto
  },
  data() {
    return {
      prod: {
        nome: "",
        fabricante: "",
        volume: {
          altura: "",
          largura: "",
          profundidade: ""
        },
        unidade: "",
        estoque: ""
      }
    };
  },
  methods: {
    addProduto() {
      const newProd = {
        id: uuid.v4(),
        nome: this.prod.nome,
        fabricante: this.prod.fabricante,
        volume: {
          altura: this.prod.volume.altura,
          largura: this.prod.volume.largura,
          profundidade: this.prod.volume.profundidade
        },
        unidade: this.prod.unidade,
        estoque: this.prod.estoque
      };
      this.prod.nome = "";
      this.prod.fabricante = "";
      this.prod.volume.altura = "";
      this.prod.volume.largura = "";
      this.prod.volume.profundidade = "";
      this.prod.unidade = "";
      this.prod.estoque = "";
      this.$emit("addProduto", newProd);
    }
  },
  props: ["listaprodutos"]
};
</script>
