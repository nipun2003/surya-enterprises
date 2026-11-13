<script setup lang="ts">
import ContactLink from './components/ContactLink.vue'
import { whatsappUrl } from './whatsapp'
</script>

<template>
  <header class="site-header">
    <a class="brand" :href="whatsappUrl" target="_blank" rel="noopener noreferrer" aria-label="Surya Enterprises on WhatsApp (opens in a new tab)">
      <svg viewBox="0 0 48 48" fill="none" aria-hidden="true">
        <circle cx="24" cy="24" r="8" />
        <path d="M24 3v7m0 28v7M3 24h7m28 0h7M9 9l5 5m20 20 5 5m0-30-5 5M14 34l-5 5" />
      </svg>
      <span>SURYA<small>ENTERPRISES</small></span>
    </a>
    <span class="header-tagline">A little style. A little sunshine.</span>
  </header>
  <main>
    <a class="banner" :href="whatsappUrl" target="_blank" rel="noopener noreferrer" aria-label="Explore clothing with Surya Enterprises on WhatsApp (opens in a new tab)">
      <img
        src="https://images.unsplash.com/photo-1602810318383-e386cc2a3ccf?auto=format&fit=crop&w=1600&q=85"
        alt="A collection of everyday shirts"
        fetchpriority="high"
        width="1600"
        height="600"
      />
      <p>Everyday clothing. Better prices.</p>
    </a>

    <section class="contact-section" aria-labelledby="brand-heading">
      <p class="brand-label">LOOK GOOD. FEEL GOOD.</p>
      <h1 id="brand-heading">Surya Enterprises</h1>
      <p class="intro">For designs, prices & orders, just WhatsApp us.</p>

      <div class="offers" aria-label="Our offers">
        <div><strong>12% <span>OFF</span></strong><p>on your first order</p></div>
        <div><strong>10% <span>OFF</span></strong><p>on every order</p></div>
      </div>

      <ContactLink />
      <p class="contact-note">1 minute response | Best product service</p>
    </section>
  </main>

  <footer>© {{ new Date().getFullYear() }} Surya Enterprises</footer>
</template>
