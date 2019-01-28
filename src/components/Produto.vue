<template >
  <tr class="produto">
    <th>{{produto.nome}}</th>
    <th>{{produto.fabricante}}</th>
    <th>
      {{produto.volume.altura}}
      {{produto.volume.largura}}
      {{produto.volume.profundidade}}
    </th>
    <th>{{produto.unidade}}</th>
    <th>{{produto.estoque}}</th>
    <th>
      <button class="del" @click="$emit('del-produto', produto.id)">x</button>
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

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
