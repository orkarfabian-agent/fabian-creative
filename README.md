# Orkar Fabian Portfolio — Starter

## Run

Open `index.html` in a browser, or serve the folder with any static server.

## Assets

- `assets/fabianimage.jpeg` — Orkar Fabian image used in the hero and LifBix work card.
- `images/oshanodes/fb_reel_1105194645432610.png` — 16:9 Oshanodes video preview; clicking it opens the video on X.
- `images/onchain/onchain_preview.png` — Onchain Festival website preview used on desktop and in its case study.
- `images/onchain/onchainmobile.jpg` — mobile-specific Onchain Festival website preview for the Selected Work card.

## Current structure

- Conversion-focused hero
- Selected work
- Oshanodes campaign links
- Onchain Festival case study
- LifBix speaking/publicity section
- Funding Access Masterclass
- Services
- About
- Lead CTA
- Social links
- Responsive mobile layout
- Neon-ready project/media architecture
- Oshanodes screenshot preview from `images/oshanodes/`, linking to the playable X video, with a Facebook Reel link as an alternative
- Onchain Festival website screenshot preview from `images/onchain/`, linking to the live site
- LifBix work-card portrait and Instagram video in its case study

## Next development step

Convert the static project cards into dynamic Neon PostgreSQL data:
projects -> media -> testimonials -> speaking -> leads. (allow people give testimonoals with their images and name and country)
Use Next.js + Drizzle + Neon for the production version.

Set up this Neon project in the current working directory.

1. `npm i -g neon@latest && neon login`
2. `neon skills -y`
3. `neon mcp -y`
4. `neon link --project-id curly-unit-41662644 --branch production -y`
5. `neon config init`
6. Update `neon.ts`:

```ts
import { defineConfig } from "@neon/config/v1";

export default defineConfig({
  auth: true,
  preview: {
    // Upgrade to a paid plan to enable AI Gateway for your project.
    // aiGateway: true,
    buckets: {
      assets: { access: "private" },
    },
    functions: {
      api: { name: "api", source: "./hello.ts" },
    },
  },
});
```

and `hello.ts`:

```ts
export default async function hello(): Promise<Response> {
  return new Response("Hello from Neon Functions");
}
```

7. `neon deploy`
