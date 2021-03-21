# Decoupled Views
_Viewing Views in Vue with DruxtJS!_


## Part 1 - Setup Drupal 9 (Quickstart).

Download and install **Drupal** using **Composer**, **`quick-start`** and the **Umami installation profile**.

1. Ceate Drupal 9 codebase:

   ```
   yes | composer create-project -s dev drupal/recommended-project:9.1.x drupal-9 && cd $_
   ```

2. Add [JSON:API Views](https://www.drupal.org/project/jsonapi_views) module:

    ```
    composer require drupal/jsonapi_views
    ```

3. Quickstart Drupal installation (Umami profile):

    ```
    php -d memory_limit=-1 web/core/scripts/drupal quick-start demo_umami
    ```

4. Install JSON:API Views module:

    http://127.0.0.1:8888/admin/modules#edit-modules-other


## Part 2 - Backend demonstration.

Demonstrate the **JSON:API Views** module functionality using the **Recipes** view.

1. Views UI:

    http://127.0.0.1:8888/admin/structure/views/view/recipes

    * [ ] Change pagination settings to 3 items per page.
    * [ ] Expose **ID** / `nid` sort.
    * [ ] Add and expose **Ingredients** / `field_ingredients_value` filter with `Contains` operator.

2. JSON:API Views - Endpoint per **View** and **Display**:

    `/jsonapi/views/{{ viewId }}/{{ display }}`

    - http://127.0.0.1:8888/jsonapi/views/recipes/default
    - http://127.0.0.1:8888/jsonapi/views/recipes/page_1

3. Pagination query:

    Next / Previous links included in JSON:API.

    `/jsonapi/views/{{ viewId }}/{{ display }}?page={{ page }}`

    - http://127.0.0.1:8888/jsonapi/views/recipes/page_1?page=0
    - http://127.0.0.1:8888/jsonapi/views/recipes/page_1?page=1

4. Sorting query:

    `/jsonapi/views/{{ viewId }}/{{ display }}?views-sort[sort_by]={{ sort }}&views-sort[sort_order]={{ ASC|DESC }}`

    - http://127.0.0.1:8888/jsonapi/views/recipes/page_1?views-sort[sort_by]=nid
    - http://127.0.0.1:8888/jsonapi/views/recipes/page_1?views-sort[sort_by]=nid&views-sort[sort_order]=DESC

5. Exposed filters query:

    `/jsonapi/views/{{ viewId }}/{{ display }}?views-filter[{{ filter }}]={{ value }}`

    - http://127.0.0.1:8888/jsonapi/views/recipes/page_1?views-filter[field_ingredients_value]=chicken
    - http://127.0.0.1:8888/jsonapi/views/recipes/page_1?views-filter[field_ingredients_value]=egg


### Part 3 - Setup Druxt in Drupal.

Download and install the **DruxtJS** Drupal module, so a frontend can be connected to the backend.

1. Add DruxtJS Drupal module:

    ```
    composer require drupal/druxt:^1.0@beta
    ```

2. Install DruxtJS module:

    http://127.0.0.1:8888/admin/modules#module-druxt

3. Add `Access DruxtJS JSON:API resources` permission:

    http://127.0.0.1:8888/admin/people/permissions/anonymous#module-druxt


### Part 4 - Setup Nuxt.js.

Download and install **Nuxt.js** and required Nuxt modules.

1. Create Nuxt codebase:

    ```
    npx create-nuxt-app nuxt && cd $_
    ```

2. Add [Druxt Views](https://views.druxtjs.org) module:

    ```
    yarn add druxt-views
    ```
    or
    ```
    npm i druxt-views
    ```

3. Install and configure module:

    `nuxt.config.js`
    ```
    modules: [
      ...
      'druxt-views',
    ],

    druxt: {
      baseUrl: 'http://127.0.0.1:8888',
    },
    ```

4. (optional) Add @nuxtjs/proxy.

    ```
    yarn add -D @nuxtjs/proxy
    ```
    or
    ```
    npm i -D @nuxtjs/proxy
    ```

    `nuxt.config.js`
    ```
    modules: [
      ...
      '@nuxtjs/storybook',
    ],

    proxy: {
      '/sites/default/files': 'http://127.0.0.1:8888'
    },
    ```

5. (optional) Add @nuxtjs/storybook.

    ```
    yarn add -D @nuxtjs/storybook
    ```
    or
    ```
    npm i -D @nuxtjs/storybook
    ```

6. (optional) Add nuxt-storybook-proxy.

    _Included in repo, @see https://github.com/nuxt-community/storybook/issues/235_

    ```
    modules: [
      ...
      '~/../assets/nuxt-storybook-proxy',
    ]
    ```


### Part 5 - Frontend demonstration.

1. Run Nuxt.

    ```
    yarn dev
    ```
    or
    ```
    npm run dev
    ```

2. (optional) Run Storybook.

    ```
    yarn nuxt storybook
    ```
    or
    ```
    npx nuxt storybook
    ```
