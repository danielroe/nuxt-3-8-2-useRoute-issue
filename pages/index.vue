<template>
  <form @submit.prevent="handleSubmit">
    <input
      v-model="goTo"
      placeholder="Write a value to test" />
    <input
      type="submit"
      value="Use navigateTo()" />

    <NuxtLink :to="link"> Use &lt;NuxtLink /&gt; </NuxtLink>
  </form>
</template>

<script>
export default {
  data() {
    return {
      goTo: "testing",
    };
  },

  computed: {
    link() {
      return `/${this.goTo}`;
    },
  },

  methods: {
    async handleSubmit() {
      await navigateTo(this.link);
    },
  },
};
</script>
