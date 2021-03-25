# Performance enhancing Druxt

Reduce JSON:API query with module settings.


## Druxt Views `query` settings.
* `bundleFilter` - Tries to determine resource types automatically.
* `fields` - Manual array of fields to filter.
* `resourceTypes` - Manual array of resource type to filter.

`nuxt.config.js`
```js
module.exports = {
  druxt: {
    views: {
      query: {
        bundleFilter: true,
        fields: ['changed', 'path', 'title']
      },
    },
  },
}
```

`DruxtView[ViewId][DisplayId].vue`
```vue
<script>
export default {
  druxt: {
    query: {
      bundleFilter: false,
      fields: ['title']
      resourceTypes: ['node--article'],
    },
  },
}
</script>
```