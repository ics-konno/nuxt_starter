<script setup lang="ts">
const route = useRoute();

const { data: page } = await useAsyncData(`page-${route.path}`, () => {
	return queryCollection("content").path(route.path).first();
});

const { data: all } = await useAsyncData("all", () =>
	queryCollection("content").all(),
);

if (!page.value) {
	throw createError({
		statusCode: 404,
		statusMessage: "Page not found",
		fatal: true,
	});
}
</script>

<template>
  <div v-for="item in all">
    {{item.title}}
  </div>
  <div>
    <NuxtLink to="/blog">Blog</NuxtLink>
  </div>
  <ContentRenderer
    v-if="page"
    :value="page"
  />
</template>
