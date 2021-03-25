<template>
  <b-button-toolbar class="mb-3">
    <b-button-group class="ml-1">
      <b-button
        v-for="sort of $attrs.sorts"
        :key="sort.id"
        @click="$emit('input', sort.id)"
      >{{ sort.expose.label }}</b-button>
    </b-button-group>
  </b-button-toolbar>
</template>
