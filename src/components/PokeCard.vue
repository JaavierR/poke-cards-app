<template>
  <div class="mx-auto max-w-sm text-center capitalize">
    <div class="relative bg-white rounded-xl shadow-lg">
      <img
        :src="pokemon.front_default"
        :alt="pokemon.name"
        class="absolute inset-x-0 mx-auto h-48 transform -translate-y-28"
      />
      <div class="space-y-7 border-b border-gray-200 pt-24 px-10 pb-10">
        <div class="space-y-3">
          <span class="text-2xl tracking-wide text-green-700 font-semibold">
            {{ pokemon.name }}
          </span>
          <div
            class="bg-gradient-to-r from-green-700 to-green-500 h-[0.35rem] mx-auto w-40 rounded-full"
          ></div>
          <div class="space-x-10 text-gray-600 pb-1 text-xs font-medium">
            <span>HP {{ hp }}</span>
            <span>EXP {{ pokemon.base_experience }}</span>
          </div>
        </div>
        <button
          class="uppercase text-xs bg-gradient-to-r from-green-500 to-green-700 py-2 px-10 rounded-full text-white font-bold tracking-widest"
        >
          Transfer
        </button>
        <div class="flex flex-wrap text-sm space-x-5">
          <div class="flex flex-col">
            <span>{{ type }}</span>
            <span class="capitalize text-xs text-gray-500"> Type </span>
          </div>
          <span class="border-l" aria-hidden></span>
          <div class="flex flex-col">
            <span>{{ weight }}</span>
            <span class="capitalize text-xs text-gray-500"> Weight </span>
          </div>
          <span class="border-l" aria-hidden></span>
          <div class="flex flex-col">
            <span>{{ height }}</span>
            <span class="capitalize text-xs text-gray-500"> Height </span>
          </div>
        </div>
      </div>
      <div class="px-10 py-4 flex flex-wrap justify-center space-x-12 text-sm">
        <div class="flex flex-col">
          <span>{{ Math.floor(Math.random() * 10000 + 1) }}</span>
          <span>Stardust</span>
        </div>
        <div class="flex flex-col">
          <span>{{ Math.floor(Math.random() * 500 + 1) }}</span>
          <span>{{ pokemon.name }} candy</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PokeCard",
  props: {
    pokemon: {
      type: Object,
      required: true,
    },
  },
  computed: {
    hp() {
      return `${this.pokemon.stats[0].base_stat}/${this.pokemon.stats[0].base_stat}`;
    },
    weight() {
      return `${(this.pokemon.weight / 10).toFixed(2)}Kg`;
    },
    type() {
      return this.pokemon.types.length > 1
        ? `${this.pokemon.types[0].type.name} / ${this.pokemon.types[1].type.name}`
        : this.pokemon.types[0].type.name;
    },
    height() {
      return `${(this.pokemon.height / 1000).toFixed(2)}m`;
    },
  },
};
</script>
