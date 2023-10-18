<template>
  <div class="centered-content">
    <h1 class="title">Carlos Ezequiel Meyer Medina 7B</h1>
    <div class="cipher-container">
      <h1 class="subtitle">Cifrado de Transposición en Vue y la libreria crypto-js</h1>
      <div>
        <label for="inputText">Mensaje:</label>
        <input id="inputText" v-model="inputText" />
      </div>
      <div>
        <label for="shift">Desplazamiento:</label>
        <input id="shift" type="number" v-model="shift" />
      </div>
      <button @click="encrypt" class="btn-cifrar">Cifrar</button>
      <button @click="decrypt" class="btn-descifrar">Descifrar</button>
      <div>
        <h2>Resultado:</h2>
        <p class="result">{{ result }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import CryptoJS from 'crypto-js';

export default {
  data() {
    return {
      inputText: "",
      shift: 0,
      result: ""
    };
  },
  methods: {
    encrypt() {
      this.result = CryptoJS.AES.encrypt(this.inputText, this.shift.toString()).toString();
    },
    decrypt() {
      this.result = CryptoJS.AES.decrypt(this.result, this.shift.toString()).toString(CryptoJS.enc.Utf8);
    }
  }
};
</script>

<style>
.centered-content {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.title {
  color: #007BFF; /* Color azul */
}

.subtitle {
  color: #28a745; /* Color verde */
}

.cipher-container {
  background-color: #f8f9fa; /* Color gris claro */
  padding: 20px;
  border-radius: 5px;
}

.btn-cifrar {
  background-color: #007BFF; /* Color azul */
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
}

.btn-descifrar {
  background-color: #dc3545; /* Color rojo */
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
}

.result {
  background-color: #e9ecef; /* Color gris claro */
  padding: 10px;
  border-radius: 5px;
}
</style>

