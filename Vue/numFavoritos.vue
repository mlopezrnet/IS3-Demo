<template>
  <div>
    <h2>Mis números favoritos</h2>
    <input v-model="numero" placeholder="Agregar número" />
    <button @click="addNumero" :disabled="esNumExistente">Agregar</button>
    <ul>
      <li v-for="(numero, index) in numFavoritos" :key="index">{{ numero }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero: "",
      numFavoritos: [],
    };
  },
  computed: {
    esNumExistente() {
      return this.numFavoritos.includes(parseInt(this.numero));
    },
  },
  methods: {
    addNumero() {
      if (!this.esNumExistente) {
        this.numFavoritos.push(parseInt(this.numero));
        this.numero = "";
      }
    },
  },
};
</script>
