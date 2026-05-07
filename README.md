# Flowryd Deal Room — FLOW-009 Tokenised MMF

**Flowryd OS** · Confidential · Not for distribution

---

## Overview

Interactive Deal Room for **FLOW-009 — Tokenised MMF**, built on the canonical FlowrydOS architecture.

Two sections:

1. **Workflow · Standards Alignment** — 8-step issuance sequence mapped to DAS Interop (ALP), ICMA BDT v1.2, SEC/CFTC taxonomy (Release 33-11412, March 2026), and Canton CIPs
2. **Transaction Volume Model** — Interactive calculator for primary issuance (FLOW-009) and secondary market activity (trading, collateral reuse, FLOW-001 intraday repo)

---

## Stack

- Single-file static HTML — no dependencies, no build step
- Fonts loaded from Google Fonts (IBM Plex Mono · Libre Franklin)
- Password-gated on load
- Deployable to Vercel, Netlify, or any static host

---

## Repo structure

```
/
├── index.html       # Deal Room — password-gated, self-contained
├── vercel.json      # Vercel static deployment config
└── README.md
```

---

## Deploy to Vercel

### One-click (recommended)

Push this repo to GitHub, then import at [vercel.com/new](https://vercel.com/new). No configuration needed — Vercel detects static HTML automatically.

### CLI

```bash
npm i -g vercel
vercel --prod
```

---

## Standards reference

| Standard | Scope | Source |
|---|---|---|
| DAS Interop (ALP) | Asset Lifecycle & Movement, Assets & Liabilities, Ownership Recognition, Legal & Regulatory Compliance | DTCC · Clearstream · Euroclear · BCG (March 2026) |
| ICMA BDT v1.2 | Party · Instrument · Pricing · Legal | ICMA PMIP |
| SEC/CFTC Release 33-11412 | Digital Securities · Digital Tools · Stablecoins · Digital Commodities | SEC/CFTC (March 2026) |
| CIP-56 | Canton token standard | Canton Network |
| CIP-0103 | dApp-to-wallet connectivity | Canton Network |

---

## Flow architecture

```
Functions → Flows → Accelerators → Code
```

- **FLOW-009** (Tokenised MMF) — 8 steps · Status: DESIGN · Target: ACCELERATOR post-MVP
- **FLOW-001** (Intraday Repo) — activated at FLOW-009 Step 8 (Collateral Agent)

---

## Transaction model methodology

| Input | Calculation |
|---|---|
| Subscriptions / day | `× steps per transaction` (4–8 Canton ledger commits per FLOW-009 cycle) |
| Redemptions / day | `× 2` (registry update + cash release) |
| Secondary trades / day | `× 1` (atomic Canton transfer) |
| Collateral reuse velocity | `trades × reuse multiplier` (GDF sandbox: 2–3x intraday) |
| Repo settlements / day | `× 8` (FLOW-001 step count per settlement cycle) |

All inputs are indicative. Refinement required once fund details are confirmed.

---

*Built on FlowrydOS canonical model · Canton Network · Mainnet*
