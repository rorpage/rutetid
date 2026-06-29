# Rutetid 🚌

Live Norwegian transit map powered by the [Entur API](https://developer.entur.org).

## Project structure

```
rutetid/
├── api/
│   ├── vehicles.js   # Proxy → api.entur.io/realtime/v2/vehicles/graphql
│   └── journey.js    # Proxy → api.entur.io/journey-planner/v3/graphql
├── public/
│   └── index.html    # The entire frontend
├── vercel.json
└── package.json
```

## Deploy to Vercel

### Option A: Vercel CLI

```bash
npm i -g vercel
cd rutetid
vercel
```

Follow the prompts. Vercel auto-detects the `api/` folder as serverless functions
and serves `public/` as static files.

### Option B: GitHub + Vercel dashboard

1. Push this folder to a GitHub repo
2. Go to [vercel.com](https://vercel.com) → New Project → Import your repo
3. Leave all settings as defaults and click Deploy

That's it. No environment variables needed — Entur's API is free and open.

## How it works

The browser calls `/api/vehicles` and `/api/journey` (your own Vercel functions).
Each function forwards the GraphQL query to Entur and returns the response.
This sidesteps CORS entirely since the request originates server-side.

```
Browser → /api/vehicles (Vercel function) → api.entur.io
Browser → /api/journey  (Vercel function) → api.entur.io
```

## Features

- Live vehicle positions (buses, trams, metro, rail, ferries) refreshed every 15s
- Stop markers with live departure boards
- Oslo, Bergen, Trondheim, Stavanger
- Mode filters
- Dark map theme

## Entur API docs

- Vehicles: https://developer.entur.org/pages-real-time-vehicle/
- Journey Planner: https://developer.entur.org/pages-journeyplanner-journeyplanner/

## Contributing

See [AGENTS.md](./AGENTS.md) for coding standards and workflow rules that apply to both human contributors and AI agents working on this project.
