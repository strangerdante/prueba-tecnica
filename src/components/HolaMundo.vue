<template>
  <div>
    <div id="contenedor">
      <div class="bloque1">
        <p>Este es el Bloque 1 dentro del contenedor.</p>
      </div>
      <div class="bloque2">
        <p>
          Este es el contenido del Bloque 2 dentro del contenedor, este contiene
          mas texto, por eso debe ser mas largo.
        </p>
      </div>
      <div class="clear"></div>
    </div>
    <div class="bloque1">
      <p>Este es el Bloque 1 fuera del contenedor.</p>
    </div>
    <div class="bloque2">
      <p>Este es el Bloque 2 fuera del contenedor.</p>
    </div>
    <div class="v-container">
      <div
        v-for="(item, index) in myArray"
        :key="item.id"
        v-show="index % 2 !== 0"
        :style="{ backgroundColor: index % 2 !== 0 ? '#e6e6e6' : '' }"
      >
        Nombre: {{ item.name }}, roles: {{ item.roles.join(", ") }}
      </div>
    </div>
    <div class="btn" @click="click">Generar</div>
    <div class="output">
      {{ output }}
    </div>
  </div>
</template>

<script>
export default {
  name: "SupportView",
  data() {
    return {
      myArray: [
        { id: 1, name: "Andres", roles: [1, 2] },
        { id: 2, name: "Andrea", roles: [5, 6] },
        { id: 3, name: "Felipe", roles: [7, 8] },
        { id: 4, name: "Santiago", roles: [8, 3] },
        { id: 5, name: "Raul", roles: [1, 9] },
      ],
      output: "",
    };
  },
  computed: {
    total() {
      return this.myArray.length;
    },
  },
  methods: {
    click() {
      this.output = `el total de listado es: ${this.total}`;
    },
  },
};
</script>

<style>
body {
  text-align: center;
  font-size: 12px;
}

#contenedor {
  width: 600px;
  margin: 0 auto 10px auto;
  padding: 10px;
  border: 1px dotted gray;
  border-radius: 6px;
}

.bloque1,
.bloque2 {
  padding: 5px;
  border-radius: 6px;
}

#contenedor .bloque1,
#contenedor .bloque2 {
  float: left;
  margin: 5px;
  width: 100px;
}

#contenedor .bloque1 {
  margin-top: 70px;
}

.bloque1 {
  background-color: red;
  color: white;
}

.bloque2 {
  background-color: yellow;
  color: black;
}

#contenedor .bloque1 p {
  font-style: italic;
}

.bloque2 p {
  font-weight: bold;
}

p {
  padding: 10px;
}

.clear {
  clear: both;
}

.btn {
  cursor: pointer;
  padding: 15px 30px;
  margin: 20px 15px;
  background-color: #2196f3;
  color: white;
  display: inline-block;
  border-radius: 6px;
  border: none;
  transition: background-color 0.3s ease;
  font-size: 16px;
  font-weight: 500;
}

.btn:hover {
  background-color: #1976d2;
}

.v-container {
  width: 600px;
  margin: 20px auto;
}

.v-container > div {
  padding: 10px;
  margin: 5px 0;
  text-align: left;
  border-radius: 6px;
}

.bloque1:not(#contenedor .bloque1),
.bloque2:not(#contenedor .bloque2) {
  width: 600px;
  margin: 10px auto;
}
</style>
