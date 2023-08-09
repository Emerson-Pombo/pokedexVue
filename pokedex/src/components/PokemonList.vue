<script setup>
import { ref, computed, defineProps } from 'vue';
import axios from 'axios';

const props = defineProps({
    searchTerm: String
});

const pokemonList = ref([]);

const fetchPokemon = async () => {
    try {
        const response = await axios.get("https://pokeapi.co/api/v2/pokemon");
        pokemonList.value = response.data.results;
    } catch (error) {
        console.error("Erro ao buscar Pokémon", error);
    }
};

const filteredPokemonList = computed(() => {
    if (!props.searchTerm) {
        return pokemonList.value;
    } else {
        return pokemonList.value.filter(pokemon =>
            pokemon.name.includes(props.searchTerm.toLowerCase())
        );
    }
});

fetchPokemon();
</script>
  
<template>
    <div>
        <ul>
            <li v-for="pokemon in filteredPokemonList" :key="pokemon.name">
                {{ pokemon.name }}
            </li>
        </ul>
    </div>
</template>
  
  