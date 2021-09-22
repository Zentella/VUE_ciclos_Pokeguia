<template>
  <div>
    {{ fotoMovAbil }}

    <div class="container">
      <div class="tarea">
        Nombre:
        <input type="text" v-model="texto" placeholder="nombre pokemón" v-on:keyup.enter="Buscar" />
        <button @click="Buscar">Buscar</button>
      </div>

      <div class="listaOk" v-if="listaOk">
        <img :src="imagen" v-bind:alt="imagen" />
        <h3>Movimientos</h3>
        <div v-for="item in moves" :key="item.id">
          <span>{{ item }}</span>
        </div>

        <h3>Habilidades</h3>
        <div v-for="item in abil" :key="item.id">
          <span>{{ item }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      listaOk: true,
      texto: "",
      nombre_pokemon: "pikachu",
      moves: [],
      abil: [],
      imagen: "",
    };
  },
  methods: {
    Buscar() {
      this.nombre_pokemon = this.texto;
      this.texto = "";      
      this.listaOk = "!this.listaOk";
    },
  },

  created() {
    fetch(`https://pokeapi.co/api/v2/pokemon/${this.nombre_pokemon}`)
      .then((response) => response.json())
      .then((json) => {
      });
  },
  computed: {
    fotoMovAbil() {
      this.moves = [];
      this.abil = [];
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.nombre_pokemon}`)
        .then((response) => response.json())
        .then((json) => {

          this.imagen = json.sprites.front_default;

          json.moves.forEach((i) => {
            this.moves.push(i.move.name);
          });

          json.abilities.forEach((i) => {
            this.abil.push(i.ability.name);
          });
        });
    },
  },
};
</script>

