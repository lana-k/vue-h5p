<template>
  <div class="wrapper">
    <input
      v-model="locale"
      type="radio"
      value="en"
    >EN
    <input
      v-model="locale"
      type="radio"
      value="de"
    >DE
    <h5p
      :key="locale"
      src="/h5p/"
      :l10n="translations[locale]"
      icon
      copyright
      export="true"
      @xapi="log"
    >
      Loading...
      <template #404="{ response }">
        {{ response.url + ' ' + response.statusText }}
      </template>
    </h5p>
  </div>
</template>

<script>
import H5p from '@src/h5p.vue'

export default {
  name: 'Example',
  components: {
    H5p
  },
  data () {
    return {
      locale: 'en',
      translations: {
        en: {},
        de: {
          reuse: 'Wiederverwenden',
          reuseContent: 'Content Wiederverwenden'
        }
      }
    }
  },
  methods: {
    log (ev) {
      console.log('received xapi statement', ev)
    }
  }
}
</script>

<style>
.wrapper {
  height: 98vh;
}
</style>
