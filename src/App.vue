<template>
  <div id="app">
    <img
      alt="Vue logo"
      src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQseV0_tE4bbw66l7c_Yz_entfI5r_fyFpKeq_4v0Hcw70JUXB2"
    >
    <br>
    <br>
    <br>
    <br>
    <br>
    <ListaProdutos
      v-bind:listaprodutos="lista_de_produtos"
      v-on:addProduto="addProduto"
      v-on:del-produto="deleteProduto"
    />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import ListaProdutos from "./components/ListaProdutos.vue";
import uuid from "uuid";

export default {
  name: "app",
  components: {
    HelloWorld,
    ListaProdutos
  },
  data() {
    return {
      lista_de_produtos: [
        {
          id: uuid.v4(),
          nome: "Halls",
          fabricante: "Mondelēz International",
          volume: {
            altura: 100,
            largura: 25,
            profundidade: 15
          },
          unidade: 324,
          estoque: "A3-12"
        },
        {
          id: uuid.v4(),
          nome: "Trident",
          fabricante: "Mondelēz International",
          volume: {
            altura: 80,
            largura: 40,
            profundidade: 5
          },
          unidade: 122,
          estoque: "A3-13"
        },
        {
          id: uuid.v4(),
          nome: "Tic Tac",
          fabricante: "Ferrero SpA",
          volume: {
            altura: 50,
            largura: 25,
            profundidade: 10
          },
          unidade: 62,
          estoque: "D23-3"
        }
      ]
    };
  },
  methods: {
    deleteProduto(id) {
      this.lista_de_produtos = this.lista_de_produtos.filter(
        prod => prod.id != id
      );
    },
    addProduto(novoProduto) {
      this.lista_de_produtos = [...this.lista_de_produtos, novoProduto];
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
