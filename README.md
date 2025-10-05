# Open Agent Payment Protocol (OAPP) — v0.1

**OAPP** is a lightweight, open protocol for **agentic commerce**.  
It defines a set of signed JSON mandates that let humans delegate product discovery, cart management, and checkout to AI agents with clear consent, cryptographic integrity, and an auditable trail of events.

It’s an **open alternative** to early frameworks like **ACP (Agentic Commerce Protocol)** and **AP2 (Agent Payments Protocol)**.  
Those frameworks are helping define the foundations of AI-driven payments, but this space is still wide open — and there’s room for multiple interoperable standards to emerge across different markets, ecosystems, and payment rails.

OAPP is fully open source. You can **build on it, fork it, or extend it** to fit your own stack.  
All we ask is that you **credit the project** and keep it open for the wider web community.

---

## Core Concepts

- **Intent Mandate** — captures human goals and purchase constraints  
- **Cart Mandate** — represents the agent’s proposal with itemised totals and proofs  
- **Payment Mandate** — provides scoped authorisation to execute the approved cart  

Each mandate is self-contained, cryptographically signed, and portable between different agent environments.

---

## Repository Contents

This repository includes the formal specification, JSON schemas, a browser-based builder, CLI toolkit, and integration guides for popular platforms.

```text
oapp/
├─ LICENSE
├─ README.md
├─ CONTRIBUTING.md
├─ spec/
│  ├─ oapp-v0.1.md
│  └─ json-schema/
│     ├─ intent.schema.json
│     ├─ cart.schema.json
│     └─ payment.schema.json
├─ examples/
│  ├─ intent.json
│  ├─ cart.json
│  └─ payment.json
├─ tools/
│  ├─ builder/            # Static web builder
│  │  ├─ index.html
│  │  ├─ styles.css
│  │  └─ app.js
│  └─ cli/
│     ├─ package.json     # ajv, tweetnacl, yargs
│     ├─ oapp-keygen.js   # generate Ed25519 keypair
│     ├─ oapp-sign.js     # sign mandates
│     └─ oapp-verify.js   # schema + signature verify
└─ adapters/
   ├─ stripe.md
   ├─ shopify.md
   └─ woocommerce.md
```

---

## Why OAPP Exists

Agentic commerce is the next step for digital trade.  
As AI models gain browsing, reasoning, and transaction capabilities, **payment protocols** must evolve to support secure and transparent AI-driven commerce.

OAPP aims to make that evolution **human-centred**, **privacy-respecting**, and **platform-neutral**.

### Highlights

- Human-first consent with explicit expiry  
- Portable JSON over any transport (HTTP, WebSocket, MCP, etc.)  
- Ed25519 signatures and hash-chained mandates  
- Minimum disclosure using PSP tokens  
- Replay protection and audit trail  
- Vendor and payment rail agnostic  
- Ready for AI-to-AI (A2A) and Model Context Protocol (MCP) integration  

---

## Getting Started

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
# Generate a keypair (for dev use)
node oapp-keygen.js > devkey.json

# Sign JSON mandate
node oapp-sign.js --key devkey.json --in ../../examples/intent.json --out ../../examples/intent.signed.json
```

### 3) Run the Builder locally

```bash
cd tools/builder
python3 -m http.server 8080
```

Then open [http://localhost:8080](http://localhost:8080) to build and export new mandates visually.

---

## Contributing

Contributions are open.  
If you’re working on AI commerce, payments, or agent frameworks — **fork it, experiment, and share** what you build.

Potential areas for contribution:
- New payment gateway adapters  
- Verification and signing modules  
- Browser or plugin integrations  
- Additional schema variants  

Pull requests, issues, and ideas are all welcome.

---

## Versioning

This is **v0.1**, published **2025-10-05**.  
Expect iteration and community discussion as agentic commerce continues to grow and standards evolve.

---

## Attribution

If you use OAPP or reference it in your own projects, please include credit:  

**“Based on the Open Agent Payment Protocol (OAPP) – an open standard initiated by Chris Lever SEO.”**

---

**#AgenticCommerce #AICommerce #OAPP #OpenSource #ProtocolDesign**
