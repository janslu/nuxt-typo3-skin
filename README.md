# nuxt-typo3-skin

Proof of concept additional theming for [nuxt-typo3](https://github.com/TYPO3-Initiatives/nuxt-typo3)

## Features
+ Storybook
+ Tailwind.css 
+ Postcss 
+ Ready to use as nuxt module

## Theme installation
in your nuxt-typo3 project

```
yarn add nuxt-typo3-skin
```

`nuxt.config.js`:
```js
...
modules: [
    'nuxt-typo3-skin',
    // Doc: https://github.com/TYPO3-Initiatives/nuxt-typo3
    'nuxt-typo3'
],
...
```

And use our [layouts/default.vue]('/src/layouts/default.vue)

```html
<template>
  <div class="wrapper">
    <header-main>
      <template v-slot:before>
        <language-switcher
          :active="currentLanguage"
          :languages="availableLanguages"
          class="container flex justify-end"
        />
      </template>
      <template v-slot:logo>
        <nuxt-link :to="navMain.link" class="flex h-full items-center">
          <logo />
        </nuxt-link>
      </template>
      <template v-slot:navigation>
        <navigation-main :links="navMain.children" />
      </template>
    </header-main>
    <div class="section-main">
      <div v-if="breadcrumbs" class="border-b mb-20px">
        <breadcrumbs :links="breadcrumbs" class="container" />
      </div>
      <nuxt />
    </div>
    <footer-main>
      <template v-slot:credits>
        <nuxt-link :to="navMain.link" class="flex h-full items-center">
          <logo />
        </nuxt-link>
      </template>
    </footer-main>
  </div>
</template>
<script>
import {
  NavigationMain,
  Logo,
  HeaderMain,
  FooterMain,
  Breadcrumbs,
  LanguageSwitcher
} from 'nuxt-typo3-skin/components'
import { mapState } from 'vuex'
export default {
  components: {
    NavigationMain,
    HeaderMain,
    FooterMain,
    Logo,
    Breadcrumbs,
    LanguageSwitcher
  },
  computed: {
    ...mapState({
      navMain: (state) => state.typo3.initial.navigation[0] || [], // get first instance from root tree,
      breadcrumbs: (state) => state.typo3.page.page.breadcrumbs || [], // get breadcrumbs for current page,
      currentLanguage: (state) => state.typo3.locale,
      availableLanguages: (state) => state.typo3.page.languages
    })
  }
}
</script>
```