# Suvarna Gold Loan Portal

A compact full-stack take-home implementation for gold-loan intake. Node/Express API with Zod validation, React/Vite responsive portal, guided assistant, and admin list. Data is persisted to a local JSON file to make first-run setup simple; for production use PostgreSQL migrations and transactional duplicate protection.

## Start

```sh
npm install
cp .env.example .env
npm run dev
```

Open http://localhost:5173. API runs on http://localhost:3001. `npm test`, `npm run eval`, and `npm run build` are available.

## API

- `GET /api/v1/loan-schemes`
- `POST /api/v1/quotes` — pure quote, no write
- `POST /api/v1/leads` — validates and recalculates server-side; supports `Idempotency-Key`; returns 409 for a recent duplicate
- `GET /api/v1/leads` — newest first with mobile numbers masked

Money values are calculated in integer paise; eligible loan is floored to whole rupees. Mock 24K rate: ₹7,000/g. Loan-to-value is capped at 75%.

## Assistant note

The Loan Assistant is a guided, deterministic UI assistant, not an LLM. It calls the same scheme, quote, and lead endpoints used by the form and asks for confirmation before submission. This avoids fabricated arithmetic and keeps setup key-free. The assignment's production LLM function-calling integration remains future work; connect a server-side provider and expose the same three validated tools before claiming an LLM agent is implemented.

## AI log

See [AI_LOG.md](./AI_LOG.md). No API key is required or included.

## More time

Replace JSON storage with PostgreSQL and migrations, add transactional uniqueness for concurrent duplicate submissions, add a real server-side LLM tool-calling loop, improve automated evals, and add rate limiting and accessibility review.
