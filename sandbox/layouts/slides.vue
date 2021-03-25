<template>
  <b-container class="d-flex flex-column min-vh-100">
    <b-navbar fixed>
      <b-navbar-brand>
        <Logo class="float-left w-25 h-25 mr-3" />
        <h4>Decoupled Vuews</h4>
        <small>Viewing Views in Vue</small>
      </b-navbar-brand>
    </b-navbar>

    <b-row class="my-auto" align-v="center">
      <b-col>
        <Nuxt />
      </b-col>
    </b-row>

    <b-row class="my-5">
      <b-col>
        <b-pagination-nav
          v-model="model"
          align="center"
          :pages="slides"
          use-router
        />
      </b-col>
    </b-row>

    <b-row class="my-3">
      <b-col>
        <b-nav>
          <b-nav-item href="https://druxtjs.org">DruxtJS.org</b-nav-item>
          <b-nav-item href="https://twitter.com/DruxtJS">@DruxtJS</b-nav-item>
          <b-nav-item href="https://github.com/druxt">
            github.com/druxt
          </b-nav-item>
          <b-nav-item href="https://discord.druxtjs.org">
            discord.druxtjs.org
          </b-nav-item>
          <b-nav-item>#druxt</b-nav-item>
        </b-nav>
      </b-col>
      <b-col class="ml-auto text-right">
        <Realityloop />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data: () => ({
    model: null,
    slides: [
      { link: '/slides', text: 'Introduction' },
      { link: '/slides/me', text: 'Who I am' },
      { link: '/slides/decoupling', text: 'Decoupling Drupal' },
      { link: '/slides/jsonapi_views', text: 'JSON:API Views' },
      { link: '/slides/druxt', text: 'DruxtJS' },
      { link: '/slides/druxt_views', text: 'DruxtViews' },
      { link: '/slides/scenario', text: 'Do the thing' },
      { link: '/slides/performance', text: 'Performance' },
      { link: '/slides/outro', text: 'Outroduction' },
    ],
  }),
}
</script>

<style scoped>
.navbar-brand {
  font-family: 'Quicksand', sans-serif;
}

.navbar-brand h4 {
  margin-bottom: -0.25rem;
}
</style>
