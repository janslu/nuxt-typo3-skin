<script>
import CeHeaderBase from 'nuxt-typo3/lib/templates/components/content/elements/CeHeader.vue'
export default {
  extends: CeHeaderBase
}
</script>
<style lang="postcss">
/* purgecss start ignore */
.ce-header {
  &--center {
    @apply text-center;
  }

  &--left {
    @apply text-left;
  }

  &--right {
    @apply text-right;
  }
}
/* purgecss end ignore */
</style>
