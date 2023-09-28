<template>
  <div>
    <h2>Mis números favoritos</h2>
    <input v-model="numero" placeholder="Agregar número" />
    <button @click="addNumero" :disabled="validarNum">Agregar</button>
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
    validarNum() {
      return this.esNumExistente || this.numero.length == 0 || isNaN(parseInt(this.numero));
    },
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

<style scoped>
/* Estilos opcionales para el componente */
ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 5px;
}

button:disabled {
  background-color: lightgray;
  cursor: not-allowed;
}
</style>
