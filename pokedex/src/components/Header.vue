<script setup>
import { ref, defineProps, defineEmits } from 'vue';

const props = defineProps({
    searchTerm: String
});

const searchTerm = ref(props.searchTerm);
const emit = defineEmits();

const handleSearch = () => {
    emit('search', searchTerm.value.toLowerCase());
};
</script>
<template>
    <header class="app-header">
        <h1 class="app-title">Pokédex</h1>
        <nav class="app-nav">
            <input v-model="searchTerm" @input="handleSearch" placeholder="Pesquisar Pokémon" />
        </nav>
    </header>
</template>
  
<style scoped>
.app-header {
    background-color: #ffcb05;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.app-title {
    font-size: 1.5rem;
    margin: 0;
}
</style>
  