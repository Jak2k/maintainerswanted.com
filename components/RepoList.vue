<script lang="ts" setup>
const topic = "maintainer-wanted";

const { data, pending, error, refresh } = await useFetch(`https://api.github.com/search/repositories?q=topic%3A${topic}`);
</script>

<template>
  <h2>Found Repositories</h2>
  <p v-if="pending" class="pending"><span class="loader"></span></p>
  <p v-if="false" class="error">Error: {{ error }}</p>
  <button @click="refresh" class="refresh">Refresh</button>
  <ul v-if="data" class="list">
    <RepoCard v-for="repo in data.items" :key="repo.id" :repo="repo" />
  </ul>
</template>