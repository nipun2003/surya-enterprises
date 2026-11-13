<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(defineProps<{
  productId?: string
  label?: string
  compact?: boolean
}>(), { label: 'Contact Us', compact: false })

const whatsappUrl = computed(() => {
  const message = `Hi sir,\nI'd like to know about ${props.productId ?? '[product/design ID]'}.`
  return `https://wa.me/918294245725?text=${encodeURIComponent(message)}`
})
</script>

<template>
  <a :href="whatsappUrl" class="contact-link" :class="{ compact }" target="_blank" rel="noopener noreferrer" :aria-label="`${label} on WhatsApp (opens in a new tab)`">
    <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M20.5 11.6a8.6 8.6 0 0 1-12.7 7.5L3 20.5l1.4-4.7A8.6 8.6 0 1 1 20.5 11.6Z" /><path d="M8.3 7.2c-.5.1-1 1-1 1.7 0 2.8 3.8 6.6 6.5 6.6.8 0 1.7-.5 1.9-1.1l.2-1-2.2-1-1 1c-1.3-.6-2.4-1.7-3-3l1-1-1.1-2.2Z" /></svg>
    <span>{{ label }}</span><span v-if="!compact" class="contact-arrow" aria-hidden="true">↗</span>
  </a>
</template>
