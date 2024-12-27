<template>
  <div class="home">
    <h1>Rechercher un utilisateur GitHub</h1>
    <input v-model="username" placeholder="Entrez un nom d'utilisateur" />
    <button @click="fetchRepos">Rechercher</button>

    <div v-if="repos.length > 0" class="repos-list">
      <RepositoryCard v-for="repo in repos" :key="repo.id" :repo="repo" />
    </div>
    <p v-else>Pas de repository trouvé.</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import axios from 'axios';
import RepositoryCard from '@/components/RepositoryCard.vue';

export default defineComponent({
  name: 'Home',
  components: { RepositoryCard },
  setup() {
    const username = ref('');
    const repos = ref([]);

    const fetchRepos = async () => {
      if (!username.value) return;

      try {
        const response = await axios.get(`https://api.github.com/users/${username.value}/repos`);
        repos.value = response.data;
      } catch (error) {
        console.error('Erreur lors de la récupération des repositories :', error);
      }
    };

    return { username, repos, fetchRepos };
  },
});
</script>

<style>
.home {
  text-align: center;
  margin: 20px;
}
input {
  padding: 8px;
  margin-right: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
button {
  padding: 8px 12px;
  background-color: #007acc;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #005f99;
}
.repos-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
