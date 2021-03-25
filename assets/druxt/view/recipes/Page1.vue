<template>
  <b-container>
    <!-- Header start -->
    <b-jumbotron
      header="DruxtJS Views"
      lead="Viewing Views in Vue"
    >
      <p>For more information visit <a href="https://views.druxtjs.org">views.druxtjs.org</a></p>
      <b-button variant="primary" href="https://views.druxtjs.org">More Info</b-button>
    </b-jumbotron>
    <!-- Header end -->

    <b-container>
      <b-row align-h="end">
        <!-- Sorts start -->
        <slot name="sorts" />
        <!-- Sorts end -->
      </b-row>
    </b-container>

    <b-row class="mb-3">
      <!-- Results start -->
      <slot name="results" :wrapper="{
        class: 'mb-3',
        component: 'b-col',
        propsData: { cols: 4 },
      }" />
      <!-- Results end -->
    </b-row>

    <b-row>
      <b-col>
        <!-- Pager -->
        <slot name="pager" />
      </b-col>
    </b-row>
  </b-container>
</template>
