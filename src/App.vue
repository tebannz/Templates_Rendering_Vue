<template>
  <div id="app">
    <form>
      <div>
        <label>Color de fondo</label>
        <input v-model="colorDeFondo" />
      </div>
      <div>
        <label>Color de texto</label>
        <input v-model="colorDeTexto" />
      </div>
      <div>
        <span> Mostrar texto <input type="checkbox" v-model="textShow" /></span>
      </div>
      <div>
        <label>Borde</label>
        <input type="range" min="0" max="150" v-model="borde" />
      </div>

      <div>
        <label>Contenido textual</label>
        <textarea v-model="contenidoTextual"></textarea>
      </div>

      <div>
        <label>Tipografía</label>
        <select v-model="tipografia">
          <option :value="tipografia" v-for="tipografia in tipografias">
            {{ tipografia }}
          </option>
        </select>
      </div>
      <div>
        <label>Opaco <input type="checkbox" v-model="opaco" /></label>
      </div>

      <div>
        <label> Tamaño de letra </label>
        <div>
          <input
            type="radio"
            name="tamaño"
            value="16px"
            v-model="tamañoDeTexto"
          />
          <label>Pequeño</label>
          <input
            type="radio"
            name="tamaño"
            value="25px"
            v-model="tamañoDeTexto"
          />
          <label>Mediano</label>
          <input
            type="radio"
            name="tamaño"
            value="40px"
            v-model="tamañoDeTexto"
          />
          <label>Grande</label>
        </div>
      </div>
    </form>

    <main>
      <div
        class="figura"
        :style="{
          background: colorDeFondo,
          borderRadius: borde + 'px',
          color: colorDeTexto,
          fontFamily: tipografia,
          fontSize: tamañoDeTexto,
        }"
        :class="{ opaco }"
      >
        <p v-show="textShow">{{ contenidoTextual }}</p>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      colorDeFondo: "black",
      colorDeTexto: "white",
      borde: "50",
      tipoDeFigura: "",
      contenidoTextual: "Bla bla bla",
      tamañoDeTexto: "",
      tipografia: "",
      textShow: true,
      tipografias: ["fantasy", "cursive", "monospace"],
      opaco: "",
    };
  },
};
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: grid;
  grid-template-columns: 400px 1fr;
  height: 100vh;
}

main {
  display: flex;
  justify-content: center;
  align-items: center;
}

.figura {
  width: 30vw;
  height: 30vw;
  display: fleX;
  align-items: center;
  justify-content: center;
}

form {
  background: darkslategray;
  color: white;
  display: flex;
  flex-direction: column;
  gap: 15px;
  padding: 40px;
}

form > div {
  display: flex;
  flex-direction: column;
  text-align: left;
}

.opaco {
  opacity: 0.5;
}
</style>
