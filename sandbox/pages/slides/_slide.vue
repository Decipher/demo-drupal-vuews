<template>
  <NuxtContent :document="slide" />
</template>

<script>
export default {
  layout: 'slides',

  data: () => ({
    slide: null,
  }),

  async fetch() {
    this.slide = await this.$content(
      this.$route.params.slide || 'intro'
    ).fetch()
  },
}
</script>

<style>
.nuxt-content svg {
  width: 100%;
}

.nuxt-content h1 {
  font-family: 'Quicksand', sans-serif;
  text-align: center;
}

.nuxt-content h1 + * {
  text-align: center;
  margin-bottom: 5rem;
}

.nuxt-content h2 {
  font-family: 'Quicksand', sans-serif;
  margin: 2rem 0 1rem;
}

.nuxt-content h2 + * {
  text-align: left;
}

.nuxt-content blockquote {
  text-align: center;
}
</style>
