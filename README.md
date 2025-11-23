NPC Validator Node

The NPC Validator Node secures the Bluesignal Pollution Gateway network. It validates incoming water-quality data from field devices, maintains block integrity, and issues rewards to node operators. This node is a core component of Bluesignal’s decentralized environmental monitoring system.

Features

Data Validation
Verifies signed sensor packets from Pollution Gateways.

Consensus Participation
Maintains block history, prevents tampering, and ensures data integrity.

Reward Distribution
Calculates and issues NPC rewards to active validators.

Device & Marketplace APIs
Exposes JSON-RPC and REST endpoints for registry, marketplace, and monitoring services.

Lightweight Deployment
Optimized for VPS or local operation.

Architecture Overview
Pollution Gateway ──► Node Validator ──► Blockchain
                          │
                          ├──► Marketplace API
                          ├──► Device Registry
                          └──► Reward Engine


The validator sits between field devices and the blockchain, ensuring only valid data is written and only legitimate operators are rewarded.

Requirements

Node.js 18+

npm or pnpm

Linux/macOS recommended (Windows works via WSL2)

Installation
git clone https://github.com/bluesignal/Node.git
cd Node
npm install

Configuration

Create a .env file in the repo root:

VALIDATOR_KEY=<your_private_key>
RPC_ENDPOINT=<blockchain_rpc>
MARKETPLACE_URL=<marketplace_api>
REGISTRY_URL=<registry_service>
REWARD_INTERVAL=600


Config parameters:

VALIDATOR_KEY — private key used to sign validator messages

RPC_ENDPOINT — blockchain RPC endpoint

MARKETPLACE_URL — API endpoint for device/credit interactions

REGISTRY_URL — device identity & provisioning service

REWARD_INTERVAL — reward distribution frequency (seconds)

Running the Validator
Development
npm run dev

Production
npm run start

API Endpoints
Health Check

GET /health
Returns online/offline status.

Submit Data Packet

POST /validate
Validates a water-quality sensor packet from a Pollution Gateway.

Validator Status

GET /status
Reports staking status, uptime, and reward metrics.

Metrics

GET /metrics
Prometheus-compatible metrics for monitoring.

Reward Logic (High-Level)

Rewards scale with uptime and successful data validations

Replayed or malformed packets are rejected

Operators earn NPC only when the node remains online and synced

Rewards settle on-chain at the end of each interval

Development Notes

Keep commits small and descriptive

No secrets in source control — use .env

Follow the existing logging and error-handling patterns

TypeScript migration under consideration

Roadmap

 Dedicated Bluesignal RPC provider

 Slashing for malicious validators

 Multi-validator consensus

 Operator dashboard + analytics

 Automatic updater for long-running nodes

License

MIT License.

Support

For issues, operational guidance, or documentation requests:
hi@bluesignal.xyz
