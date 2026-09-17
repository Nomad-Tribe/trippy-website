<p align="center">
  <strong>🧭 Trippy</strong><br>
  <em>Travel solo, never alone.</em>
</p>

<p align="center">
  <a href="https://nomad-tribe.github.io/trippy-website/">Live Showcase</a> ·
  <a href="https://trippy-494087041610.asia-south1.run.app/">Open App</a> ·
  <a href="https://github.com/Nomad-Tribe/Trippy">Parent Monorepo</a>
</p>

---

## What is Trippy?

**Trippy** is an AI-powered solo-travel platform where travellers find group trips or build their own, match with compatible travellers on overlapping dates, and book hosted trips directly from travel communities across India.

Solo travel shouldn't mean travelling alone. Trippy connects 12,400+ solo travellers and 1,800+ riders across 47 destinations — from Spiti Valley and Leh-Ladakh to Goa and the Western Ghats.

## Core Features

| Feature | Description |
|---|---|
| 🤖 **AI Compatibility Matcher** | Find travellers with overlapping dates and compatible travel styles — ranked by a compatibility score based on budget, personality, interests, and pace. |
| 🗺️ **DIY Trip Builder** | Pick a hostel, find compatible travellers checking in the same week, form a group, and build a shared itinerary with expense splitting. |
| 🏍️ **Motorcycle & Road Trip Hub** | Set up your bike or car profile, match with co-riders on identical dates, share live GPS tracking, log waypoint check-ins, and use emergency SOS alerts. |
| 🏔️ **Hosted Group Trips** | Browse 340+ curated group trips from verified travel communities & riding clubs — Himalayan Wolves, Coastal Nomads, and 80+ operators. |
| 💼 **Partner CRM** | Travel communities and operators list group departures, manage bookings, and connect with 12,000+ active travellers & riders. No listing fees. |

## Tech Stack

| Layer | Technology |
|---|---|
| Build | [Vite 6](https://vitejs.dev/) — lightning-fast HMR and optimised production bundles |
| Icons | [Phosphor Icons](https://phosphoricons.com/) — `ph-bold` default weight |
| Styling | Modern CSS with custom properties (design tokens), no frameworks |
| Typography | [Bricolage Grotesque](https://fonts.google.com/specimen/Bricolage+Grotesque) (headings) + [Hanken Grotesk](https://fonts.google.com/specimen/Hanken+Grotesk) (body) |
| CI/CD | GitHub Actions → GitHub Pages |
| Backend | Full-stack app deployed on Google Cloud Run (separate deployment) |

## Live Showcase

🌐 **[nomad-tribe.github.io/trippy-website](https://nomad-tribe.github.io/trippy-website/)**

This is the public marketing website for Trippy. The full-stack application (consumer app, partner CRM, admin console, API) is deployed separately on Google Cloud Run.

## Architecture

This repository is a **satellite** that mirrors the `trippy/website/` subtree from the parent monorepo [`Nomad-Tribe/Trippy`](https://github.com/Nomad-Tribe/Trippy).

```
Nomad-Tribe/Trippy (parent monorepo)
└── trippy/website/          ← this satellite mirrors this subtree
    ├── index.html            ← single-page marketing site
    ├── src/styles.css         ← design tokens + all component styles
    ├── vite.config.ts         ← base: './' for GitHub Pages compatibility
    ├── package.json
    └── .github/workflows/
        └── deploy.yml         ← GitHub Pages deployment workflow
```

**Satellite repo rule:** `Nomad-Tribe/Trippy` always contains the authoritative code. Changes are pushed to this satellite via:
```bash
git subtree push --prefix trippy/website https://github.com/Nomad-Tribe/trippy-website.git main
```

## Local Development

```bash
# Clone the satellite (or work from the parent monorepo)
git clone https://github.com/Nomad-Tribe/trippy-website.git
cd trippy-website

# Install dependencies
npm install

# Start dev server (port 5174)
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Deployment

Deployment is fully automated via GitHub Actions:

1. **Push to `main`** triggers the workflow
2. Vite builds the production bundle into `./dist`
3. GitHub Pages artifact is uploaded and deployed
4. Site is live at `https://nomad-tribe.github.io/trippy-website/`

Manual deployment can also be triggered via `workflow_dispatch` in the Actions tab.

## Related Repositories

| Repo | Role |
|---|---|
| [Nomad-Tribe/Trippy](https://github.com/Nomad-Tribe/Trippy) | Parent monorepo — single source of truth |
| **Nomad-Tribe/trippy-website** | ← You are here (marketing website satellite) |
| Nomad-Tribe/trippy-mobile | React Native iOS + Android app (planned) |
| Nomad-Tribe/trippy-data | Trip aggregation pipeline (planned) |
| Nomad-Tribe/trippy-infra | Cloud deployment configs, CI/CD (planned) |

---

<p align="center">
  <strong>© 2026 Trippy</strong> · Travel solo, never alone · Made in India 🇮🇳<br>
  Built by <a href="https://github.com/Nomad-Tribe">Nomad Tribe</a>
</p>
