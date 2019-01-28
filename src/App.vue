<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
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
          id: 1,
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
          id: 2,
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
          id: 3,
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
      console.log(novoProduto);
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
