<template>
  <v-form>
    <v-textarea
      @keyup="generarBase64"
      solo
      name="texto"
      v-model="texto"
      label="Texto"
    ></v-textarea>
    <v-textarea
      @keyup="generarTexto"
      solo
      name="textoBase64"
      v-model="textoBase64"
      label="Base64"
    ></v-textarea>
  </v-form>
</template>

<script>
export default {
  name: "Contactos",
  data() {
    return {
      msg: "Listado de contactos",
      texto: "",
      textoBase64: ""
    };
  },
  methods: {
    generarBase64() {
      this.textoBase64 = btoa(this.texto);
    },
    generarTexto() {
      try {
        this.texto = atob(this.textoBase64);
      } catch (error) {
        this.texto = "Base64 inválido";
      }
    }
  }
};
</script>
