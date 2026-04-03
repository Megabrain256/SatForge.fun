# SatForge.fun — Complete Project Files
Bitcoin-Native OP-20 Token Launchpad on OP_NET
Built April 2026 · satforge.fun

---

## What's in this zip

### /website — Standalone HTML Pages (deploy immediately)
No build step needed. Drop these in any static host or Vercel.

| File | Page | Purpose |
|------|------|---------|
| index.html | Landing / Coming Soon | Mailchimp signup, countdown, ember particles |
| satforge-home.html | Homepage (app) | Hero, stats, live token grid |
| satforge-explore.html | Explore | Full token feed, leaderboard, search/filter |
| satforge-launch.html | Launch Token | 3-step form: configure → confirm → deploy |
| satforge-token.html | Token Detail | Price chart, buy/sell, holders, trades |
| satforge-account.html | My Account | Portfolio, holdings, creator earnings |
| satforge-docs.html | Documentation | Non-technical platform overview |
| satforge-preview.html | UI Preview | All pages in one tabbed preview |

All pages are cross-linked and share the same design system
(Bebas Neue + IBM Plex Mono + Barlow, Bitcoin orange palette, grain overlay).

---

### /nextjs-app — Full Next.js 14 App (production-ready)
```
app/
  page.tsx                    Homepage
  explore/page.tsx            Explore page
  create/page.tsx             Launch form
  account/page.tsx            Account / portfolio
  token/[slug]/page.tsx       Token detail page
  not-found.tsx               Custom 404
  api/
    tokens/route.ts           GET/POST /api/tokens
    tokens/[slug]/route.ts    GET/PATCH /api/tokens/[slug]
    deployments/route.ts      PATCH /api/deployments
    trades/route.ts           POST /api/trades
    cron/
      sync-deployments/       Every 5 min — confirm token deploys
      sync-trades/            Every 2 min — index trading events

components/
  Navbar.tsx   Ticker.tsx   StatsBar.tsx   Footer.tsx
  TokenFeed.tsx   Leaderboard.tsx   LaunchForm.tsx   Portfolio.tsx
  token/
    PriceChart.tsx   TradeCard.tsx   TokenInfo.tsx
    TradesFeed.tsx   TopHolders.tsx

hooks/
  useOPWallet.ts              OP_WALLET connect/disconnect/state

lib/
  opnet.ts                    OP_NET provider, contract helpers, types
  db.ts                       Supabase client + typed DB helpers
  mock.ts                     Mock data (replace with real queries)

contracts/
  SatForgeContracts.ts        AssemblyScript OP-20 factory + token

supabase/
  migration_001_initial.sql   Run this in Supabase SQL Editor

.gitignore
vercel.json
.env.local.example
```

#### Quick start
```bash
cd nextjs-app
cp .env.local.example .env.local
# Fill in SUPABASE_URL, SUPABASE_ANON_KEY, SUPABASE_SERVICE_KEY
npm install
npm run dev
```

---

### /docs-pdf — Documentation PDFs
| File | Contents |
|------|---------|
| SatForge_Documentation.pdf | Full technical + non-technical platform docs (15 pages) |
| SatForge_Launch_Costs.pdf | Complete mainnet cost breakdown with breakeven analysis (8 pages) |

---

## Deploy checklist

- [ ] Run `supabase/migration_001_initial.sql` in Supabase SQL Editor
- [ ] Add env vars to Vercel (see .env.local.example)
- [ ] Deploy factory contract to OP_NET testnet → test → mainnet
- [ ] Set `NEXT_PUBLIC_FACTORY_ADDRESS` in Vercel env vars
- [ ] Point Hostinger DNS to Vercel (A record: 76.76.21.21)
- [ ] Seed one token with real liquidity on MotoSwap
- [ ] Wire Mailchimp in index.html (MC_U, MC_ID, MC_DC)

---

© 2026 SatForge.fun · Built on OP_NET · Bitcoin-native OP-20 Token Launchpad
