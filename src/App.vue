<script setup lang="ts">
import { computed, ref } from 'vue'
import ContactLink from './components/ContactLink.vue'

const categories = ['All styles', 'Shirts', 'T-shirts', 'Layers'] as const
type Category = (typeof categories)[number]
const selectedCategory = ref<Category>('All styles')

// Sample editorial styles; replace with the brand's actual catalog and photography.
const products = [
  { id: 'SE-001', name: 'The everyday shirt', category: 'Shirts', detail: 'Easy-going. Always in style.', image: 'photo-1598033129183-c4f50c736f10', alt: 'Classic neutral button-down shirt', tag: 'EVERYDAY ESSENTIAL' },
  { id: 'SE-002', name: 'The classic tee', category: 'T-shirts', detail: 'Your off-duty uniform.', image: 'photo-1521572163474-6864f9cf17ab', alt: 'Minimal white cotton T-shirt', tag: 'LESS, BUT BETTER' },
  { id: 'SE-003', name: 'The weekend layer', category: 'Layers', detail: 'A little extra, effortlessly.', image: 'photo-1543076447-215ad9ba6923', alt: 'Casual jacket with considered details', tag: 'THE FINISHING TOUCH' },
  { id: 'SE-004', name: 'The relaxed shirt', category: 'Shirts', detail: 'Room to make it your own.', image: 'photo-1602810318383-e386cc2a3ccf', alt: 'A selection of relaxed button-down shirts', tag: 'WARDROBE REGULAR' },
]
const visibleProducts = computed(() => products.filter(
  (product) => selectedCategory.value === 'All styles' || product.category === selectedCategory.value,
))
const photo = (id: string, width: number) => `https://images.unsplash.com/${id}?auto=format&fit=crop&w=${width}&q=85`
</script>

<template>
  <a class="skip-link" href="#main">Skip to content</a>
  <div class="announcement">
    <span>A little welcome gift. <strong>12% off your first order.</strong></span>
    <span class="announcement-extra">Good style. Even better value.</span>
  </div>

  <header class="site-header">
    <a class="brand" href="#" aria-label="Surya Enterprises home">
      <svg class="brand-sun" viewBox="0 0 48 48" fill="none" aria-hidden="true">
        <circle cx="24" cy="24" r="8" />
        <path d="M24 3v7m0 28v7M3 24h7m28 0h7M9 9l5 5m20 20 5 5m0-30-5 5M14 34l-5 5" />
      </svg>
      <span>SURYA<span class="brand-small">ENTERPRISES</span></span>
    </a>
    <nav aria-label="Main navigation">
      <a href="#collection">The collection</a>
      <a href="#our-story">Our story</a>
    </nav>
    <ContactLink class="header-contact" compact />
  </header>

  <main id="main">
    <section class="hero" aria-labelledby="hero-heading">
      <div class="hero-copy">
        <p class="eyebrow"><span class="small-line"></span> GOOD CLOTHES. GREAT DAYS.</p>
        <h1 id="hero-heading">Everyday style,<br />a little <em>brighter.</em></h1>
        <p class="hero-description">For the everyday moments and everything in between. Find your next favourite with Surya Enterprises.</p>
        <div class="hero-offers">
          <div><strong>12% <span>OFF</span></strong><p>on your first order</p></div>
          <span class="offer-divider" aria-hidden="true"></span>
          <div><strong>10% <span>OFF</span></strong><p>on every order</p></div>
        </div>
        <ContactLink />
        <p class="contact-note">1 minute response | Best product service</p>
        <a class="text-link hero-explore" href="#collection">Find your everyday favourite <span aria-hidden="true">↗</span></a>
      </div>
      <div class="hero-visual">
        <img class="hero-image hero-image-main" :src="photo('photo-1516257984-b1b4d707412e', 1100)" alt="Everyday menswear styled with a relaxed, timeless feel" fetchpriority="high" />
        <div class="hero-image-secondary">
          <img :src="photo('photo-1598033129183-c4f50c736f10', 600)" alt="A closer look at an everyday button-down shirt" />
          <span>THE EVERYDAY EDIT / 01</span>
        </div>
        <div class="hero-sticker"><span>A GOOD DAY</span><svg viewBox="0 0 48 48" fill="none" aria-hidden="true"><circle cx="24" cy="24" r="8" /><path d="M24 3v7m0 28v7M3 24h7m28 0h7M9 9l5 5m20 20 5 5m0-30-5 5M14 34l-5 5" /></svg><span>STARTS HERE</span></div>
        <div class="image-caption"><span>Wear what feels like you.</span><span>01 — 04</span></div>
      </div>
    </section>

    <div class="benefit-strip" aria-label="Shopping benefits">
      <span><span aria-hidden="true">✦</span> Everyday versatility</span>
      <span><span aria-hidden="true">✦</span> Styles worth repeating</span>
      <span><span aria-hidden="true">✦</span> Order on WhatsApp</span>
      <span><span aria-hidden="true">✦</span> A personal touch, always</span>
    </div>

    <section id="collection" class="collection section-space" aria-labelledby="collection-heading">
      <div class="section-heading">
        <div><p class="eyebrow">THE EVERYDAY EDIT</p><h2 id="collection-heading">Meet your new <em>favourites.</em></h2></div>
        <p>Easy to wear. Easy to love.<br />Explore a little inspiration for your wardrobe.</p>
      </div>
      <div class="collection-toolbar">
        <div class="filters" role="group" aria-label="Filter styles">
          <button v-for="category in categories" :key="category" :aria-pressed="selectedCategory === category" @click="selectedCategory = category">{{ category }}</button>
        </div>
        <span class="style-count" role="status">{{ visibleProducts.length }} styles to explore</span>
      </div>
      <div class="product-grid">
        <article v-for="product in visibleProducts" :key="product.id" class="product-card">
          <div class="product-image">
            <img :src="photo(product.image, 700)" :alt="product.alt" loading="lazy" width="700" height="875" />
            <span class="product-tag">{{ product.tag }}</span>
            <ContactLink :product-id="product.id" :label="`Ask about ${product.id}`" class="product-inquiry" compact />
          </div>
          <div class="product-heading"><h3>{{ product.name }}</h3><span>{{ product.id }}</span></div>
          <p>{{ product.detail }}</p>
        </article>
      </div>
      <p class="catalog-note">A little style inspiration. Message us for current designs, prices, sizes & availability.</p>
    </section>

    <section id="our-story" class="story section-space" aria-labelledby="story-heading">
      <div class="story-heading"><p class="eyebrow">THE SURYA WAY</p><h2 id="story-heading">Not just clothes.<br /><em>A good feeling.</em></h2><p>We believe getting dressed should be the easiest part of your day. A style you love, a price that feels right, and a real person to help you choose.</p><a class="text-link" href="#contact">Let's find your style <span aria-hidden="true">↗</span></a></div>
      <div class="story-values">
        <article><span class="value-number">01 /</span><div><h3>Made for your everyday</h3><p>From slow mornings to spontaneous plans. Discover versatile styles that fit into your life.</p></div></article>
        <article><span class="value-number">02 /</span><div><h3>Good style. Thoughtful value.</h3><p>Enjoy 12% off on your first order and 10% off on every order. Your wardrobe will thank you.</p></div></article>
        <article><span class="value-number">03 /</span><div><h3>A conversation, not a checkout</h3><p>Questions about a fit or a design? Chat directly with us on WhatsApp for personal help with your order.</p></div></article>
      </div>
    </section>

    <section id="contact" class="contact-section" aria-labelledby="contact-heading">
      <div class="contact-decoration" aria-hidden="true">✳</div>
      <div><p class="eyebrow">YOUR NEXT FAVOURITE IS A MESSAGE AWAY</p><h2 id="contact-heading">Good style starts<br />with a <em>hello.</em></h2><p>Send us a design you love. We'll take it from there.</p></div>
      <div class="contact-action"><ContactLink /><p class="contact-note">1 minute response | Best product service</p><span>No carts. No complications. Just a conversation.</span></div>
    </section>
  </main>

  <footer class="site-footer">
    <a class="brand footer-brand" href="#"><span>SURYA<span class="brand-small">ENTERPRISES</span></span></a>
    <p>A little style. A little sunshine. Every day.</p>
    <span>© {{ new Date().getFullYear() }} Surya Enterprises</span>
    <a href="#main" class="back-top" aria-label="Back to top">↑</a>
  </footer>
  <div class="mobile-contact"><ContactLink compact /><span>Let's find your favourite.</span></div>
</template>
