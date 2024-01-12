<template>
  <div class="puntaje">
    <p>Puntaje: {{ puntaje }}</p>
    <p>Intento: {{ intento }}</p>
  </div>
  <div class="container">
    <Prueba
      ref="uno"
      img="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"
      texto="xxxxxxxxxxxx"
    />
    <Prueba
      ref="dos"
      img="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/2.svg"
      texto="xxxxxxxxxxxx"
    />
    <Prueba
      ref="tres"
      img="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/3.svg"
      texto="xxxxxxxxxxxx"
    />
    <div class="boton">
      <button v-on:click="juega(), comprueba(), intentos()">JUGAR</button>
    </div>
  </div>
</template>

<script>
import Prueba from "./components/prueba.vue";

export default {
  name: "App",
  components: {
    Prueba,
  },
  data() {
    return {
      puntaje: 0,
      intento: 0,
      puntos: null,
    };
  },
  methods: {
    juega() {
      this.$refs.uno.consumirApi();
      this.$refs.dos.consumirApi();
      this.$refs.tres.consumirApi();
    },

    comprueba() {
      const respuestas = [
        this.$refs.uno.texto,
        this.$refs.dos.texto,
        this.$refs.tres.texto,
      ];
      const puntos = this.puntos;
      for ( let i = 0; i < respuestas.length; i++) {
        if (respuestas[i] === "yes") {
          puntos++;
        }
      }
      if (puntos === 3) {
        this.puntaje += 5;
      } else if (puntos === 2) {
        rgis.puntaje += 2;
      } else if (puntos === 1) {
        this.puntaje += 1;
      } else if (puntos === 0) {
        this.puntaje += 0;
      }
    },
    intentos() {
      this.intento++;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.puntaje {
  display: grid;
  grid-template-columns: repeat(2, 500px);
  gap: 1px;
}
.boton {
  display: grid;
  justify-content: center;
  align-content: center;
  grid-column: 2;
}
</style>
