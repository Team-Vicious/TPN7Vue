<template>
  <div>
    <b-container fluid>
      <b-row>
        <b-col>
          <img
            style="max-height:400px"
            :src="'/images/' + instrumentoEncontrado.imagen"
        /></b-col>
        <b-col>
          <b-row>
            <b-col
              ><h1>{{ instrumentoEncontrado.instrumento }}</h1></b-col
            >
          </b-row>
          <b-row>
            <b-col
              ><h2>$ {{ instrumentoEncontrado.precio }}</h2></b-col
            >
          </b-row>
          <b-row>
            <b-col
              ><h2>{{ instrumentoEncontrado.marca }}</h2></b-col
            >
          </b-row>
         
          
          <b-row style="text-align:center">
            <b-col
              ><b-button href="/" variant="outline-primary"
                >VOLVER</b-button
              ></b-col
            >
          </b-row>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>


<script>
export default {
  name: "DetalleInstrumento",
  components: {},
  mounted() {
    this.getInstrumentoXId();
  },
  data() {
    return {
      instrumentoEncontrado: []
    };
  },
  methods: {
    async getInstrumentoXId() {
      const parametroId = this.$route.params.id;
      const res = await fetch("/instrumentos.json");
      const resJson = await res.json();
      console.log(resJson);
      this.instrumentoEncontrado = await resJson.instrumentos.find(
        instrumento => instrumento.id === parametroId
      );
      console.log(this.instrumentoEncontrado);
    }
  }
};
</script>
