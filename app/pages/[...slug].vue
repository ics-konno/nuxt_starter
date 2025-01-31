<script setup lang="ts">
const route = useRoute();

const { data: page } = await useAsyncData(`page-${route.path}`, () => {
	return queryCollection("content").path(route.path).first();
});

const { parent } = useAppConfig();

if (!page.value) {
	throw createError({
		statusCode: 404,
		statusMessage: "Page not found",
		fatal: true,
	});
}
</script>

<template>
  <p>{{parent.primary}}</p>
  <ContentRenderer
    v-if="page"
    :value="page"
  />
</template>
