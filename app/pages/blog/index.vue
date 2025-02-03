<script setup lang="ts">
const { data } = await useAsyncData("blog", () =>
	queryCollection("blog").all(),
);
</script>

<template>
  <div>
    <h1>Blog</h1>
    <ul>
      <li v-for="item in data" :key="item.id">
        <NuxtLink :to="item.path">{{ item.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>
