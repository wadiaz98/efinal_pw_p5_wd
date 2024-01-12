<template>
  <div class="container">
    
    <div class="imagenes">
      <img v-bind:src="img" />
      <p>{{texto}}</p>
    </div>
    
  </div>
</template>

<script>
export default {
  props: ["img", "texto"],
  data() {
    return {
      img: this.img,
      texto: this.texto,
    };
  },
  methods: {
    async consumirApi() {
      const { answer, image } = await fetch("https://yesno.wtf/api").then(
        (respuesta) => respuesta.json()
        
      );
      this.img = image;
      this.texto=answer;
    },
    comprueba(){
        
    }
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  grid-template-columns: repeat(3, 330px);
}
img {
  width: 200px;
  height: 200px;
}

</style>