# Surya Enterprises

A simple, mobile-first clothing landing page built with Vue 3, TypeScript, and Vite. It focuses on the brand, two offers, and one large WhatsApp contact button, with no navigation or extra sections.

## Development

Install dependencies with `bun install`, then run `bun run dev`. Run `bun run build` for a type-checked production build and `bun run preview` to preview it. The Dockerfile builds and serves the static site with nginx; no runtime API configuration is required.

## Content

- The brand logo, full banner image, and contact button all open WhatsApp at `918294245725` with the URL-encoded message `Hi sir,\nNeed Id.` The shared destination and message are in `src/whatsapp.ts`.
- The phone number is used only in the WhatsApp link destination; it is not displayed on the page.
- The banner image in `src/App.vue` is illustrative photography loaded from Unsplash. Replace it with owned brand photography for launch. Fonts use the local system stack.
- The two offers are displayed separately, not as a combined discount.
