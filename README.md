# Surya Enterprises

A mobile-first, single-page clothing storefront built with Vue 3, TypeScript, and Vite.

## Development

Install dependencies with `bun install`, then run `bun run dev`. Run `bun run build` for a type-checked production build and `bun run preview` to preview it. The Dockerfile builds and serves the static site with nginx; no runtime API configuration is required.

## Content

- The WhatsApp destination is `918294245725` in `src/components/ContactLink.vue`. General inquiries include the requested `[product/design ID]` placeholder; product inquiries include their specific design ID. All links open WhatsApp with a URL-encoded message.
- Edit the sample product list and image references in `src/App.vue` to publish the actual catalog. The current images and design IDs are illustrative, not verified inventory. The page directs customers to ask for current prices, sizes, and availability.
- Product and banner images are loaded from Unsplash; fonts are loaded from Google Fonts, with local system fallbacks. Replace images with owned brand photography for launch.
- The two offers are displayed separately, not as a combined discount.
