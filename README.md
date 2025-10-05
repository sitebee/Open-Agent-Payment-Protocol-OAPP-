# Open Agent Payment Protocol (OAPP) — v0.1

OAPP is a lightweight, open protocol for agentic commerce. It defines three signed JSON mandate types that allow humans to delegate discovery and checkout to AI agents with clear consent, security, and an auditable chain of records.

- **Intent Mandate** — human goals and constraints
- **Cart Mandate** — the agent’s proposal with itemised totals and proofs
- **Payment Mandate** — scoped authorisation to execute the approved cart

This repository includes the formal spec, JSON Schemas, a browser builder, a CLI toolkit, and integration notes.

## Quick links

- Spec: [`/spec/oapp-v0.1.md`](spec/oapp-v0.1.md)
- JSON Schemas: [`/spec/json-schema`](spec/json-schema)
- Examples: [`/examples`](examples)
- Builder (static site): [`/tools/builder`](tools/builder)
- CLI tools: [`/tools/cli`](tools/cli)

## Why OAPP

- Human-first consent with explicit expiry
- Portable JSON over any transport
- Ed25519 signatures and hash chaining
- Minimum disclosure with PSP tokens
- Replay protection and audit trail
- Vendor and rail agnostic

## Getting started

### 1) Validate example mandates
```bash
cd tools/cli
npm install
node oapp-verify.js ../../examples/intent.json
node oapp-verify.js ../../examples/cart.json
node oapp-verify.js ../../examples/payment.json
```

### 2) Sign a mandate
```bash
# Generate a keypair (dev only)
node oapp-keygen.js > devkey.json

# Sign JSON
node oapp-sign.js --key devkey.json --in ../../examples/intent.json --out ../../examples/intent.signed.json
```

### 3) Run the Builder locally
Serve `tools/builder/` with any static server, e.g.
```bash
cd tools/builder
python3 -m http.server 8080
```

## Versioning

This is **v0.1** dated 2025-10-05. Expect changes as the community provides feedback.
