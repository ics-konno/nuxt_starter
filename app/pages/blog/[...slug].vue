<script setup lang="ts">
const route = useRoute();
const { data } = useAsyncData(route.path, () =>
	queryCollection("content").path(route.path).first(),
);
</script>

<template>
<ContentRenderer v-if="data" :value="data" />
</template>

<style scoped>

</style>
