<script setup>
import { ref } from 'vue';
import Header from '@/components/Header.vue';
import PokemonList from '@/components/PokemonList.vue';

const searchTerm = ref("");

const updateSearchTerm = (term) => {
  searchTerm.value = term;
};
</script>

<template>
  <div id="app">
    <Header @search="updateSearchTerm" />
    <PokemonList :searchTerm="searchTerm" />
  </div>
</template>


