<template >
  <tr class="produto">
    <th>{{produto.nome}}</th>
    <th>{{produto.fabricante}}</th>
    <th v-if="produto.volume.altura + produto.volume.largura + produto.volume.profundidade == '' "></th>
    <th v-else-if="produto.volume.profundidade == '' ">
      <div v-if="produto.volume.altura == '' ">{{produto.volume.largura}}</div>
      <div v-else-if="produto.volume.largura == '' ">{{produto.volume.altura}}</div>
      <div v-else>{{produto.volume.altura}} x {{produto.volume.largura}}</div>
    </th>
    <th v-else-if="produto.volume.largura == '' ">
      <div v-if="produto.volume.altura == '' ">{{produto.volume.profundidade}}</div>
      <div v-else-if="produto.volume.profundidade == '' ">{{produto.volume.altura}}</div>
      <div v-else>{{produto.volume.altura}} x {{produto.volume.profundidade}}</div>
    </th>
    <th v-else-if="produto.volume.altura == '' ">
      {{produto.volume.largura}} x
      {{produto.volume.profundidade}}
    </th>
    <th v-else>
      {{produto.volume.altura}} x
      {{produto.volume.largura}} x
      {{produto.volume.profundidade}}
    </th>
    <th>{{produto.unidade}}</th>
    <th>{{produto.estoque}}</th>
    <th>
      <b-button variant="danger" @click="$emit('del-produto', produto.id)">x</b-button>
    </th>
  </tr>
</template>

<script>
export default {
  name: "Produto",
  props: ["produto"],
  methods: {}
};
</script>

<style scoped>
.produto {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
</style>
