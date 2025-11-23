No — that rendering in your screenshot is **exactly what we *don’t* want.**
GitHub collapses everything because there are **no Markdown headers (`#`)**, **no spacing**, and **no code fencing** in the right places.

I’ll fix it **properly**.

Below is a *production-grade* README that will render **exactly** like a real project at a professional startup.

**Copy/paste this EXACTLY as-is.**
Do not add/remove spaces.
Do not indent anything.

---

# NPC Validator Node

The NPC Validator Node secures the Bluesignal Pollution Gateway network. It validates incoming water-quality data from field devices, maintains block integrity, and distributes rewards to node operators.

---

## Overview

The validator node is responsible for:

* Verifying signed sensor packets from Pollution Gateway devices
* Maintaining a consistent block record
* Issuing NPC rewards to validator operators
* Exposing REST and JSON-RPC endpoints for Marketplace and Registry integrations

---

## Architecture

```
Pollution Gateway Device → Validator Node → Blockchain
                                   │
                                   ├─ Marketplace API
                                   └─ Registry Service
```

---

## Features

* Data validation
* Consensus and block integrity
* Reward distribution
* Lightweight API layer
* Runs on small VPS or local machine

---

## Requirements

* Node.js 18 or higher
* npm or pnpm
* Linux/macOS recommended (Windows via WSL2 works)

---

## Installation

```bash
git clone https://github.com/bluesignal/Node.git
cd Node
npm install
```

---

## Configuration

Create a file named **`.env`** in the root directory:

```
VALIDATOR_KEY=<your_private_key>
RPC_ENDPOINT=<blockchain_rpc>
MARKETPLACE_URL=<marketplace_api>
REGISTRY_URL=<registry_service>
REWARD_INTERVAL=600
```

### Parameter Guide

* `VALIDATOR_KEY` — private key used by the validator
* `RPC_ENDPOINT` — blockchain RPC endpoint
* `MARKETPLACE_URL` — API for device and credit interactions
* `REGISTRY_URL` — device provisioning service
* `REWARD_INTERVAL` — reward calculation interval (seconds)

---

## Running the Validator

### Development

```bash
npm run dev
```

### Production

```bash
npm run start
```

---

## API Endpoints

### Health Check

```
GET /health
```

### Validate Data Packet

```
POST /validate
```

### Validator Status

```
GET /status
```

### Metrics (Prometheus)

```
GET /metrics
```

---

## Reward Logic

* Rewards scale with uptime
* Valid packets increase score
* Invalid or replayed packets are rejected
* Rewards are issued on-chain at scheduled intervals

---

## Development Notes

* Do not commit secrets
* Keep changes small and readable
* Follow existing logging patterns
* TypeScript migration may be added later

---

## Roadmap

* Multi-validator consensus
* Slashing for malicious validators
* On-chain validation proofs
* Operator dashboard
* Auto-update support

---

## License

MIT License.

---

## Support

[hi@bluesignal.xyz](mailto:hi@bluesignal.xyz)

---

## Bluesignal

[https://bluesignal.xyz](https://bluesignal.xyz)

---
