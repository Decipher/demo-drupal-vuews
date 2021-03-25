<template>
  <b-container fluid="lg">
    <b-navbar toggleable="lg" type="dark" variant="primary">
      <b-navbar-brand href="https://views.druxtjs.org">
        DruxtJS Views
      </b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item href="https://github.com/druxt/druxt-views">
            GitHub
          </b-nav-item>
          <b-nav-item to="/slides">Slides</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <b-row>
      <b-col>
        <b-breadcrumb :items="[{ text: 'Home' }]" />
      </b-col>
    </b-row>

    <b-row>
      <!-- View start -->
      <b-container>
        <!-- <DruxtView
          display-id="page_1"
          uuid="e530624f-cc93-42ef-8fbd-7546acc64eac"
          view-id="recipes"
        /> -->

        <!-- Header start -->
        <b-jumbotron header="DruxtJS Views" lead="Viewing Views in Vue">
          <p>
            For more information visit
            <a href="https://views.druxtjs.org">views.druxtjs.org</a>
          </p>
          <b-button variant="primary" href="https://views.druxtjs.org">
            More Info
          </b-button>
        </b-jumbotron>
        <!-- Header end -->

        <b-container>
          <b-row align-h="end">
            <!-- Sorts start -->
            <b-button-toolbar class="mb-3">
              <b-button-group class="ml-1">
                <b-button>Date</b-button>
                <b-button>Title</b-button>
              </b-button-group>
            </b-button-toolbar>
            <!-- Sorts end -->
          </b-row>
        </b-container>

        <b-row class="mb-3">
          <!-- Results start -->
          <b-col v-for="key in 6" :key="key" class="mb-3" cols="4">
            <b-card
              title="Card Title"
              img-src="https://picsum.photos/600/300/?image=25"
              img-alt="Image"
              img-top
              tag="article"
            >
              <b-card-text>
                Some quick example text to build on the card title and make up
                the bulk of the card's content.
              </b-card-text>

              <b-button to="/article" variant="primary">Go somewhere</b-button>
            </b-card>
          </b-col>
          <!-- Results end -->
        </b-row>

        <b-row>
          <b-col>
            <!-- Pager -->
            <b-pagination align="center" />
          </b-col>
        </b-row>
      </b-container>
      <!-- View end -->
    </b-row>
  </b-container>
</template>
