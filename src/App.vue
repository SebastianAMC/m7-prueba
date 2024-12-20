<template>
  <TituloApp :numeroPokemones="descubiertos" />
  <br>
  <div class="divs-order" v-for="pokemon in pokemones" :key="pokemon.id">
    <PokemonesList :nombre="pokemon.name" :imagen="pokemon.img" @contador="contador()" />
  </div>
</template>

<script>
import axios from 'axios';
import PokemonesList from './components/PokemonesList.vue';
import TituloApp from './components/TituloApp.vue';

export default {
  name: 'App',
  components: {
    PokemonesList,
    TituloApp
  },
  data() {
    return {
      pokemones: [],
      descubiertos: 0
    }
  },
  mounted() {
    this.conectarApi()
  },
  methods: {
    async conectarApi() {
      const { data } = await axios.get("https://pokeapi.co/api/v2/pokemon")
      const pokeurl = data.results.map(poke => axios.get(poke.url))
      let pokedata = await Promise.all(pokeurl)

      pokedata = pokedata.map(p => {
        let data = {
          name: p.data.name,
          img: p.data.sprites.other["official-artwork"].front_default
        }
        return data;
      })

      this.pokemones = pokedata;
    },
    contador() {
      this.descubiertos++
    }
  }
}
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

.divs-order {
  display: inline-flex;
}
</style>
