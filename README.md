# Wanderlust — Intelligent Travel Discovery & Planning (MVP)

> Discover → Personalize → Plan → Connect → Book

This is a working Phase 1 MVP for the Wanderlust concept: a single platform where
a traveler enters a budget, trip length and interests, gets ranked destination
recommendations, and can generate a day-by-day itinerary with stays, food,
activities, transport and sample tour packages — all in one place.

## What's actually implemented

- **Destination discovery** — search by budget, duration and interests
- **Rule-based recommendation engine** (`src/utils/itineraryEngine.js`) that scores
  and ranks destinations against a traveler's constraints, with human-readable
  reasons for each match (a simple, explainable stand-in for the "AI personalization"
  described in the pitch — see [Future work](#future-work))
- **Destination detail pages** — attractions & hidden gems, stays, restaurants,
  activities, transport options and sample tour packages
- **Automatic itinerary generation** — pick a trip length and budget tier, get a
  day-by-day plan with an estimated total cost
- Six seeded destinations across mountains, nature/adventure, spiritual and beach
  travel styles: Darjeeling, Gangtok & Sikkim, Manali, Shillong & Meghalaya,
  Rishikesh, and Goa

All destination content (attractions, hotel tiers, prices, packages) is **sample
data** in `src/data/destinations.js`, written for demo purposes — not a live feed.
See [Where the data comes from](#where-the-data-comes-from).

## Tech stack

- [Vite](https://vitejs.dev/) + [React 18](https://react.dev/)
- [react-router-dom](https://reactrouter.com/) for the two views (discovery / detail)
- Plain CSS with a small design-token system (`src/index.css`) — no UI framework

## Running it locally

```bash
npm install
npm run dev
```

Then open the URL Vite prints (typically `http://localhost:5173`).

To build a production bundle:

```bash
npm run build
npm run preview
```

## Project structure

```
wanderlust/
├── src/
│   ├── data/destinations.js        # Sample destination dataset
│   ├── utils/itineraryEngine.js    # Matching + itinerary generation logic
│   ├── components/
│   │   ├── Navbar.jsx
│   │   ├── Home.jsx                # Hero, search form, ranked results
│   │   ├── SearchForm.jsx
│   │   ├── DestinationCard.jsx
│   │   ├── DestinationDetail.jsx   # Explore + itinerary builder
│   │   └── ItineraryView.jsx       # Day-by-day "route line" view
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── index.html
├── package.json
└── vite.config.js
```

## Where the data comes from

For this MVP, destination content is hand-curated sample data based on general,
publicly known facts about each place (attraction names, typical price bands),
so the app has something realistic to filter, rank and plan against without
depending on a paid API key. As described in the original concept doc, a
production version would replace `destinations.js` with:

- Government tourism portals / state tourism department data
- Licensed hotel, activity and transport APIs (availability + live pricing)
- Verified travel agency / local operator partnerships

No third-party platform data is scraped in this MVP.

## Future work (Phase 2 / Phase 3, per the original concept)

- Swap the rule-based matcher for a real ML/LLM-based personalization model
- Live hotel/activity/transport inventory via licensed APIs
- User accounts, saved trips, reviews & ratings
- Real-time booking + payment integration
- Business/partner dashboard for hotels, guides and local operators

## Publishing this to GitHub

This folder is not yet a git repository. To push it:

```bash
cd wanderlust
git init
git add .
git commit -m "Initial commit: Wanderlust MVP"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

(Create the empty repo on GitHub first, then swap in its URL above.)
