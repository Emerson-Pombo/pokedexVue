<script>
import axios from 'axios';

export default {
    data() {
        return {
            pokemonList: []
        };
    },
    methods: {
        async fetchPokemon() {
            try {
                const response = await axios.get("https://pokeapi.co/api/v2/pokemon");
                this.pokemonList = response.data.results;
            } catch (error) {
                console.error("Erro ao buscar Pokémon", error);
            }
        }
    },
    created() {
        this.fetchPokemon();
    }
};
</script>

<template>
    <div>
        <ul>
            <li v-for="pokemon in pokemonList" :key="pokemon.name">
                {{ pokemon.name }}
            </li>
        </ul>
    </div>
</template>