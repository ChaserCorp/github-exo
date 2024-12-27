<template>
  <div class="favorites">
    <h1>Mes Favoris</h1>
    <div v-if="favorites.length > 0" class="repos-list">
      <RepositoryCard v-for="repo in favorites" :key="repo.id" :repo="repo" />
    </div>
    <p v-else>Aucun repository mis en favori.</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
import RepositoryCard from '@/components/RepositoryCard.vue';

export default defineComponent({
  name: 'Favorites',
  components: { RepositoryCard },
  setup() {
    const favorites = ref([]);

    onMounted(() => {
      favorites.value = JSON.parse(localStorage.getItem('favorites') || '[]');
    });

    return { favorites };
  },
});
</script>

<style>
.favorites {
  text-align: center;
  margin: 20px;
}
.repos-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
