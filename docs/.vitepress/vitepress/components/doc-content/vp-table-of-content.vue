<script setup lang="ts">
import { computed } from 'vue'
import MarkdownIt from 'markdown-it'
import { useToc } from '../../composables/use-toc'

import sponsorLocale from '../../../i18n/component/sponsor.json'
import { useLang } from '../../composables/lang'
import SponsorsButton from '../sponsors/sponsors-button.vue'
import SponsorRightBigLogoList from '../sponsors/right-big-logo-list.vue'
import SponsorRightTextList from '../sponsors/right-richtext-list.vue'
import SponsorRightLogoSmallList from '../sponsors/right-logo-small-list.vue'
import tag from '../../../plugins/tag'
// import SponsorLarge from '../vp-sponsor-large.vue'

const localMd = MarkdownIt().use(tag)
const headers = useToc()
const lang = useLang()
const sponsor = computed(() => sponsorLocale[lang.value])
</script>

<template>
  <aside ref="container" class="toc-wrapper">
    <nav class="toc-content" />
  </aside>
</template>
<style scoped lang="scss">
.sponsors-button:deep {
  button {
    width: 100%;
  }
}
</style>
