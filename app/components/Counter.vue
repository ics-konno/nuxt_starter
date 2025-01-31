<template>
  <div>
    <h3>Counter: {{ count }}</h3>
    <button @click="increment">
      Increment
    </button>
    <button @click="decrement">
      Decrement
    </button>
    <p>{{ data.parent.primary }}</p>
  </div>
</template>

<script setup lang="ts">
const count = ref(0);

const increment = () => {
	count.value++;
};

const decrement = () => {
	count.value--;
};

const data = useAppConfig();
</script>

<style scoped>
button {
  margin: 5px;
}
</style>
