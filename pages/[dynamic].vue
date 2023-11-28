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

<script>
export default {
  async setup() {
    // This is just to test and it can be anything else really
    await useFetch(`https://api.publicapis.org/entries`);

    const route = useRoute();

    return {
      setupValue: route.params.dynamic,
    };
  },

  data() {
    return {
      mountedValue: null,
    };
  },

  computed: {
    documentLocation() {
      return document.location;
    },
  },

  mounted() {
    this.mountedValue = this.$route.params.dynamic;
  },
};
</script>
