<template>
  <div class="min-h-screen flex items-center justify-center">
    <PokeCard v-if="pokemon" :pokemon="pokemon" />
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

import PokeCard from "@/components/PokeCard.vue";

export default {
  name: "Home",
  components: {
    PokeCard,
  },
  data() {
    return {
      pokemon: null,
    };
  },
  mounted() {
    this.fetchPokemon(141);
  },
  methods: {
    async fetchPokemon(id) {
      const {
        data: {
          name,
          stats,
          types,
          base_experience,
          weight,
          height,
          sprites: {
            other: {
              dream_world: { front_default },
            },
          },
        },
      } = await axios.get(`https://pokeapi.co/api/v2/pokemon/${id}`);

      this.pokemon = {
        name,
        stats,
        types,
        base_experience,
        weight,
        height,
        front_default,
      };
    },
  },
};
</script>
