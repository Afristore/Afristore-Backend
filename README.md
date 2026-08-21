# Afristore-Backend

> **🟠 Priority:** High | **Difficulty:** Medium | **Estimated Effort:** 2–3 days

The Node.js backend for the [Afristore Marketplace](https://github.com/Afristore/marketplace) — extracted from the monorepo into its own dedicated repository.

This service includes:
- **Express API** — REST endpoints for listings, collections, auctions, and user data
- **Stellar Ledger Poller** — indexes on-chain events from the Soroban smart contracts
- **Crank Bot** — keep-alive bot that bumps TTLs to prevent contract storage archival
- **Redis** — pub/sub for real-time SSE notifications
- **Prisma** — ORM for PostgreSQL

---

## 🚀 Getting Started (once code is populated)

```bash
npm install
npx prisma generate
npx prisma migrate deploy
npm run dev       # Start the Express API + Poller
npm run crank     # Start the Crank keep-alive bot
```

---

## 🔧 Environment Variables

Copy `.env.example` to `.env` and fill in:

| Variable | Description |
|---|---|
| `DATABASE_URL` | PostgreSQL connection string |
| `REDIS_URL` | Redis connection string |
| `HORIZON_URL` | Stellar Horizon URL |
| `CONTRACT_ID` | Soroban Marketplace contract address |
| `NETWORK_PASSPHRASE` | Stellar network passphrase |
| `PORT` | Express server port (default: 3001) |
| `CRANK_INTERVAL_MS` | Crank bot polling interval in ms |

---

## 📋 Source Location (Monorepo)

This repository is being extracted from [`afristore/indexer/`](https://github.com/Afristore/marketplace/tree/master/indexer) in the main monorepo.

**Tracked in:** [ui-ux-issues.md — Issue 120](https://github.com/Afristore/marketplace/blob/master/ui-ux-issues.md)

---

## 🤝 Contributing

1. Fork this repository
2. Create a feature branch: `git checkout -b feat/your-feature`
3. Make your changes and ensure all CI checks pass:
   - `npm run lint` — TypeScript type-check must exit 0
   - `npm run test` — All Vitest suites must pass
4. Open a PR — **all CI must pass before a PR is eligible for review and merge**

---

## 📦 Tech Stack

- Node.js 20+ / TypeScript
- Express 5
- Prisma 5 + PostgreSQL
- Redis 4
- Stellar SDK (`@stellar/stellar-sdk`)
- Vitest (testing)

---

## 📄 License

MIT — see [LICENSE](./LICENSE)
