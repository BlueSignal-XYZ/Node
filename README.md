NPC Validator Node

The NPC Validator Node secures the Bluesignal Pollution Gateway network. It validates incoming water-quality data from field devices, maintains block integrity, and distributes rewards to node operators.

Overview

The validator node is responsible for:

Verifying signed sensor packets from Pollution Gateway devices

Maintaining a consistent block record

Issuing NPC rewards to validator operators

Exposing REST and JSON-RPC endpoints for Marketplace and Registry integrations

Architecture
Pollution Gateway Device → Validator Node → Blockchain
                                   │
                                   ├─ Marketplace API
                                   └─ Registry Service

Features

Data validation

Consensus and block integrity

Reward distribution

Lightweight API layer

Runs on small VPS or local machine

Requirements

Node.js 18 or higher

npm or pnpm

Linux/macOS recommended (Windows works via WSL2)

Installation
git clone https://github.com/bluesignal/Node.git
cd Node
npm install

Configuration

Create a .env file:

VALIDATOR_KEY=<your_private_key>
RPC_ENDPOINT=<blockchain_rpc>
MARKETPLACE_URL=<marketplace_api>
REGISTRY_URL=<registry_service>
REWARD_INTERVAL=600


Config parameters:

VALIDATOR_KEY — private key used by the validator

RPC_ENDPOINT — blockchain RPC endpoint

MARKETPLACE_URL — API for device and credit interactions

REGISTRY_URL — device provisioning service

REWARD_INTERVAL — reward calculation interval (seconds)

Running the Validator

Development

npm run dev


Production

npm run start

API Endpoints

Health Check
GET /health

Validate Data Packet
POST /validate

Validator Status
GET /status

Metrics (Prometheus)
GET /metrics

Reward Logic (Summary)

Rewards increase with uptime

Valid packets increase score

Invalid or replayed packets are rejected

Rewards are issued on-chain at scheduled intervals

Development Notes

Do not commit secrets

Keep changes small and readable

Follow existing code patterns

TypeScript migration may be added later

Roadmap

Multi-validator consensus

Slashing for malicious validators

On-chain validation proofs

Operator dashboard

Auto-update support

License

MIT License.

Support

For issues or documentation requests:
hi@bluesignal.xyz

Bluesignal

https://bluesignal.xyz
