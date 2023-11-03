<script lang="ts" setup>
defineProps<{
  repo: any;
}>();
</script>
<template>
  <li class="repo">
    <h3>
      {{ repo.full_name }}
      <span v-if="repo.stargazers_count" class="badge stars">{{ repo.stargazers_count }}</span>
      <span v-if="repo.language" class="badge lang">{{ repo.language }}</span>
      <span v-if="repo.license" class="badge license">{{ repo.license.name }}</span>
      <span v-if="repo.fork" class="badge fork">{{ repo.fork }}</span>
    </h3>
    <p>{{ repo.description }}</p>
    <a :href="repo.html_url">View on Github</a>
    <details>
      <summary>JSON</summary>
      <pre>{{ JSON.stringify(repo, null, 2) }}</pre>
    </details>
  </li>
</template>