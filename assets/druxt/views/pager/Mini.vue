<template>
  <b-pagination align="center" v-model="model" />
</template>

<script>
import { DruxtViewsPagerMixin } from 'druxt-views'

export default {
  mixins: [DruxtViewsPagerMixin],
}
</script>
