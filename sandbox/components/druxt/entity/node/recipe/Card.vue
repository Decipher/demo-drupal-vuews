<template>
  <b-card
    v-if="!$fetchState.pending"
    :title="$attrs.entity.attributes.title"
    :img-src="image.included[0].attributes.uri.url"
    img-alt="Image"
    img-top
    tag="article"
  >
    <b-card-text>
      {{ $attrs.entity.attributes.field_summary.value }}
    </b-card-text>

    <b-button to="/article" variant="primary">Go somewhere</b-button>
  </b-card>
</template>

<script>
import { DrupalJsonApiParams } from 'drupal-jsonapi-params'

export default {
  data: () => ({
    image: null,
  }),

  async fetch() {
    this.image = await this.$store.dispatch('druxt/getResource', {
      ...this.$attrs.fields.field_media_image.data.data,
      query: new DrupalJsonApiParams()
        .addFields('media--image', ['field_media_image'])
        .addInclude(['field_media_image'])
        .addFields('file--file', ['uri'])
    })
  }
}
</script>
