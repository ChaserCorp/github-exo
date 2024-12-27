<template>
    <div class="repository-card">
      <h3>{{ repo.name }}</h3>
      <p>{{ repo.description || 'Pas de description disponible' }}</p>
      <a :href="repo.html_url" target="_blank">Voir sur GitHub</a>
      <button @click="toggleFavorite">
        {{ isFavorite ? 'Retirer des Favoris' : 'Ajouter aux Favoris' }}
      </button>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref, watch } from 'vue';
  
  export default defineComponent({
    name: 'RepositoryCard',
    props: {
      repo: {
        type: Object,
        required: true,
      },
    },
    setup(props) {
      const isFavorite = ref(false);
  
      const toggleFavorite = () => {
        const favorites = JSON.parse(localStorage.getItem('favorites') || '[]');
        if (isFavorite.value) {
          const updatedFavorites = favorites.filter((fav: any) => fav.id !== props.repo.id);
          localStorage.setItem('favorites', JSON.stringify(updatedFavorites));
        } else {
          favorites.push(props.repo);
          localStorage.setItem('favorites', JSON.stringify(favorites));
        }
        isFavorite.value = !isFavorite.value;
      };
  
      watch(
        () => props.repo.id,
        () => {
          const favorites = JSON.parse(localStorage.getItem('favorites') || '[]');
          isFavorite.value = favorites.some((fav: any) => fav.id === props.repo.id);
        },
        { immediate: true }
      );
  
      return { isFavorite, toggleFavorite };
    },
  });
  </script>
  
  <style>
  .repository-card {
    border: 1px solid #ddd;
    padding: 16px;
    margin: 16px 0;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  .repository-card h3 {
    margin: 0 0 8px;
  }
  .repository-card a {
    display: inline-block;
    margin: 8px 0;
    color: #007acc;
  }
  button {
    background-color: #007acc;
    color: white;
    padding: 8px 12px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  button:hover {
    background-color: #005f99;
  }
  </style>
  