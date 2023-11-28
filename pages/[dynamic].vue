<template>
  <div>
    <p>Your [dynamic] value on setup() is: {{ setupValue }}</p>
    <p>Your [dynamic] value on mounted() is: {{ mountedValue }}</p>
    <p v-if="setupValue === mountedValue">Values match! Hooray!</p>
    <p v-else>
      It looks like values don't match as they should!
      <a :href="documentLocation">Click here to refresh</a> and it will work as
      intended.
    </p>
    <p>
      <NuxtLink to="/">Click here to go back and try other values</NuxtLink>
    </p>
  </div>
</template>

<script setup lang="ts">
// This is just to test and it can be anything else really
await useFetch(`https://api.publicapis.org/entries`);

const route = useRoute();

const setupValue = route.params.dynamic

const mountedValue = ref(null)

const documentLocation = computed(() => document.location)

onMounted(() => {
  mountedValue.value = route.params.dynamic;
})
</script>
