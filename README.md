NPC Validator Node

Bluesignal’s decentralized validation engine for the Pollution Gateway network.
Ensures data integrity, block correctness, and reward distribution across the NPC ecosystem.

<div align="center">








</div>
🌊 Overview

The NPC Validator Node secures the Bluesignal Pollution Gateway network by:

Verifying signed water-quality sensor packets

Maintaining consensus and block correctness

Issuing NPC rewards to validators

Exposing lightweight APIs for Marketplace + Registry services

This node sits at the core of Bluesignal’s distributed environmental data pipeline.

🧱 Architecture
   ┌────────────────┐       ┌────────────────┐      ┌──────────────────┐
   │ Pollution       │       │ NPC Validator  │      │   Blockchain     │
   │ Gateway Device  ├──────►│     Node       ├─────►│   (NPC Layer)    │
   └────────────────┘       └─────┬──────────┘      └────────┬─────────┘
                                   │                          │
                                   │                          │
                                   ▼                          ▼
                         ┌──────────────────┐       ┌────────────────────┐
                         │ Marketplace API  │       │   Registry Service │
                         └──────────────────┘       └────────────────────┘

✨ Features
Feature	Description
Data Validation	Confirms authenticity + structure of incoming sensor packets
Consensus Logic	Maintains a secure, append-only block record
Reward Engine	Distributes NPC rewards to participating validators
API Layer	JSON-RPC & REST endpoints for system integrations
Lightweight Deployment	Easily runs on a VPS or local machine
🔧 Requirements

Node.js 18+

npm or pnpm

Linux/macOS recommended (WSL2 works on Windows)

📦 Installation
git clone https://github.com/bluesignal/Node.git
cd Node
npm install

⚙️ Configuration

Create a .env file in the repo root:

VALIDATOR_KEY=<your_private_key>
RPC_ENDPOINT=<blockchain_rpc>
MARKETPLACE_URL=<marketplace_api>
REGISTRY_URL=<registry_service>
REWARD_INTERVAL=600


Parameter Guide

Key	Purpose
VALIDATOR_KEY	Private key for validator signing
RPC_ENDPOINT	Blockchain RPC provider
MARKETPLACE_URL	API endpoint for credit/device interactions
REGISTRY_URL	Device provisioning + identity service
REWARD_INTERVAL	Time (seconds) between reward calculations
🚀 Running the Validator
Development
npm run dev

Production
npm run start

📡 API Endpoints
Health Check
GET /health

Validate Data Packet
POST /validate

Validator Status
GET /status

Metrics (Prometheus)
GET /metrics

💰 Reward Logic (Simplified)

Uptime = higher reward weight

Valid packets increase score

Malformed / replay packets reduce score

Rewards settle on-chain every interval

All reward events are cryptographically signed

🛠️ Development Notes

Keep PRs small and reviewable

No secrets in commits

Follow existing logging patterns

TypeScript migration under evaluation

🗺️ Roadmap

 Multi-validator consensus

 Slashing for malicious validators

 On-chain proofs of validation

 Validator operator dashboard

 Auto-update support

📄 License

This project is licensed under the MIT License.

📬 Support

Questions, integration requests, or documentation needs:
hi@bluesignal.xyz

💙 Bluesignal

Visit: https://bluesignal.xyz
