# Vaultfire Ecosystem Map

> How all the pieces fit together.

Vaultfire is the trust and accountability layer for the AI agent economy — what HTTPS was to web security. This map shows how every repo in the ecosystem connects.

---

## Architecture

```
                          ┌─────────────────────────────┐
                          │      CORE PROTOCOL           │
                          │                               │
                          │   ghostkey-316-vaultfire-init  │
                          │   (source code + contracts)    │
                          └──────────────┬────────────────┘
                                         │
                    ┌────────────────────┼────────────────────┐
                    │                    │                     │
                    ▼                    ▼                     ▼
         ┌──────────────┐    ┌──────────────┐     ┌──────────────────┐
         │  CHAIN REPOS  │    │   ZK LAYER   │     │    LIVE HUB      │
         │               │    │              │     │                  │
         │ vaultfire-base │    │ vaultfire-zk │     │ theloopbreaker   │
         │ vaultfire-aval │    │   -proofs    │     │     .com         │
         │ vaultfire-arb  │    │              │     │                  │
         │ vaultfire-poly │    │ (RISC Zero)  │     │  (Agent Hub UI)  │
         └──────┬─────────┘    └──────────────┘     └────────┬─────────┘
                │                                            │
                │              ┌──────────────┐              │
                └─────────────►│  CONTRACTS   │◄─────────────┘
                               │  REGISTRY    │
                               │              │
                               │ vaultfire-   │
                               │  contracts   │
                               └──────┬───────┘
                                      │
              ┌───────────────────────┼───────────────────────┐
              │                       │                        │
              ▼                       ▼                        ▼
    ┌──────────────┐       ┌──────────────┐        ┌──────────────────┐
    │   CORE SDK   │       │  NPM PACKAGES │        │   FRAMEWORK      │
    │              │       │              │        │   INTEGRATIONS   │
    │ vaultfire-sdk│       │ vaultfire-a2a │        │                  │
    │              │       │ vaultfire-vns │        │ vaultfire-lang   │
    │ (TypeScript) │       │ vaultfire-x402│        │   chain          │
    │              │       │ vaultfire-xmtp│        │ vaultfire-crewai │
    └──────────────┘       └──────────────┘        │ vaultfire-openai │
                                                    │   -agents        │
                                                    │ vaultfire-vercel │
                                                    │   -ai            │
                                                    │ vaultfire-mcp    │
                                                    │   -server        │
                                                    └──────────────────┘
```

---

## Repository Guide

### Core Protocol

| Repo | What It Is |
|------|-----------|
| [ghostkey-316-vaultfire-init](https://github.com/Ghostkey316/ghostkey-316-vaultfire-init) | Main protocol source — all smart contracts, the trust framework, and protocol logic |
| [vaultfire-contracts](https://github.com/Ghostkey316/vaultfire-contracts) | Canonical registry of all deployed contract addresses and verified ABIs across all chains |
| [vaultfire-zk-proofs](https://github.com/Ghostkey316/vaultfire-zk-proofs) | RISC Zero ZK trust attestations — privacy-preserving proofs on all 4 chains |

### Chain Deployments

Each chain has its own partner-facing reference with deployed addresses, verification links, and chain-specific details.

| Repo | Chain | Contracts |
|------|-------|-----------|
| [vaultfire-base](https://github.com/Ghostkey316/vaultfire-base) | Base (8453) | 17 live contracts |
| [vaultfire-avalanche](https://github.com/Ghostkey316/vaultfire-avalanche) | Avalanche C-Chain (43114) | 16 live contracts |
| [vaultfire-arbitrum](https://github.com/Ghostkey316/vaultfire-arbitrum) | Arbitrum One (42161) | 17 live contracts |
| [vaultfire-polygon](https://github.com/Ghostkey316/vaultfire-polygon) | Polygon PoS (137) | 17 live contracts |

> **67 verified smart contracts across 4 mainnet chains.**

### Live Hub

| Repo | What It Is |
|------|-----------|
| [theloopbreaker.com](https://github.com/Ghostkey316/theloopbreaker.com) | The Vaultfire Agent Hub — live at [theloopbreaker.com](https://theloopbreaker.com). Agent registration, discovery, trust verification, XTMP messaging, bond creation, and protocol docs. |

### SDK & npm Packages

All published on npm under the `@vaultfire` scope. Install any of them with `npm install`.

| Repo | npm Package | Purpose |
|------|------------|---------|
| [vaultfire-sdk](https://github.com/Ghostkey316/vaultfire-sdk) | `@vaultfire/agent-sdk` | Core TypeScript SDK — identity, bonds, trust queries, multi-chain |
| [vaultfire-a2a](https://github.com/Ghostkey316/vaultfire-a2a) | `@vaultfire/a2a` | Enrich Google A2A Agent Cards with on-chain trust data |
| [vaultfire-langchain](https://github.com/Ghostkey316/vaultfire-langchain) | `@vaultfire/langchain` | LangChain/LangGraph tools for on-chain trust verification |
| [vaultfire-vns](https://github.com/Ghostkey316/vaultfire-vns) | `@vaultfire/vns` | Vaultfire Name Service — resolve .vns names on-chain |
| [vaultfire-x402](https://github.com/Ghostkey316/vaultfire-x402) | `@vaultfire/x402` | HTTP 402 trust-gated USDC payments |
| [vaultfire-xmtp](https://github.com/Ghostkey316/vaultfire-xmtp) | `@vaultfire/xmtp` | Trust-gated encrypted agent messaging via XMTP |

### Framework Integrations

Drop-in trust verification for the frameworks agents actually use.

| Repo | Framework | What It Does |
|------|-----------|-------------|
| [vaultfire-langchain](https://github.com/Ghostkey316/vaultfire-langchain) | LangChain / LangGraph | 9 tools — identity, trust, bonds, VNS, payments |
| [vaultfire-crewai](https://github.com/Ghostkey316/vaultfire-crewai) | CrewAI | On-chain trust and bonds for CrewAI agent crews |
| [vaultfire-openai-agents](https://github.com/Ghostkey316/vaultfire-openai-agents) | OpenAI Agents SDK | Trust verification tools for OpenAI agents |
| [vaultfire-vercel-ai](https://github.com/Ghostkey316/vaultfire-vercel-ai) | Vercel AI SDK | Trust-gating middleware for Vercel AI apps |
| [vaultfire-mcp-server](https://github.com/Ghostkey316/vaultfire-mcp-server) | Model Context Protocol | MCP server exposing Vaultfire tools to any MCP client |
| [vaultfire-langgraph-demo](https://github.com/Ghostkey316/vaultfire-langgraph-demo) | LangGraph | Working demo: trust-gated task delegation |

### Reference Agents

| Repo | What It Is |
|------|-----------|
| [vaultfire-agents](https://github.com/Ghostkey316/vaultfire-agents) | 3 reference agents (Sentinel, Researcher, Coordinator) with live on-chain trust verification |

### Documentation & Research

| Repo | What It Is |
|------|-----------|
| [vaultfire-docs](https://github.com/Ghostkey316/vaultfire-docs) | Developer portal — interactive docs, quickstart guides, live playground |
| [vaultfire-whitepaper](https://github.com/Ghostkey316/vaultfire-whitepaper) | Vaultfire Trust Framework whitepaper — economic accountability for the AI agent economy |
| [vaultfire-a2a-trust-extension](https://github.com/Ghostkey316/vaultfire-a2a-trust-extension) | Formal specification for adding on-chain trust to Google A2A Agent Cards |
| [vaultfire-showcase](https://github.com/Ghostkey316/vaultfire-showcase) | Why bonds beat scores — live on-chain proof, competitive analysis, economic modeling |
| [vaultfire-explorer](https://github.com/Ghostkey316/vaultfire-explorer) | Live on-chain explorer — trust scores, bonds, governance across all 4 chains |

### Enterprise & Extended

| Repo | What It Is |
|------|-----------|
| [vaultfire-enterprise](https://github.com/Ghostkey316/vaultfire-enterprise) | Bridge enterprise IAM (Okta, Azure AD) to Vaultfire on-chain agent trust |
| [vaultfire-solana](https://github.com/Ghostkey316/vaultfire-solana) | Vaultfire Protocol — 15 Solana programs (Anchor framework) |

### Origins

| Repo | What It Is |
|------|-----------|
| [hermes-vaultfire](https://github.com/Ghostkey316/hermes-vaultfire) | KYA (Know Your Agent) trust layer for Hermes AI agents |
| [openclaw-vaultfire](https://github.com/Ghostkey316/openclaw-vaultfire) | Vaultfire integration for OpenClaw AI assistant |
| [Claude-code-Vaultfire-](https://github.com/Ghostkey316/Claude-code-Vaultfire-) | Claude Code Vaultfire integration |
| [awesome-ai-safety](https://github.com/Ghostkey316/awesome-ai-safety) | Curated list of AI safety resources (fork — Vaultfire listed) |
| [Ghostkey-Humanity-Mirror](https://github.com/Ghostkey316/Ghostkey-Humanity-Mirror) | Belief-based AI agent — Open Model Hackathon entry |

---

## How It All Connects

```
An agent developer's journey:

1. READ     →  vaultfire-whitepaper, vaultfire-docs
2. EXPLORE  →  vaultfire-explorer, vaultfire-showcase
3. INSTALL  →  npm install @vaultfire/agent-sdk (or any framework package)
4. REGISTER →  theloopbreaker.com or direct contract call
5. BOND     →  Create partnership/accountability bonds on-chain
6. VERIFY   →  Any agent can query trust on-chain across 4 chains
7. BUILD    →  Use framework integrations (LangChain, CrewAI, OpenAI, Vercel AI, MCP)
```

---

## Quick Start

```bash
npm install @vaultfire/agent-sdk
```

```typescript
import { VaultfireSDK } from '@vaultfire/agent-sdk';

const vf = new VaultfireSDK({ chain: 'base' });
const agent = await vf.getAgent('0xYOUR_ADDRESS');
console.log(agent.streetCred); // 0-95
```

That's it. You're reading trust data from 4 mainnet chains.

---

## Links

- **Live Hub**: [theloopbreaker.com](https://theloopbreaker.com)
- **npm**: [@vaultfire](https://www.npmjs.com/org/vaultfire)
- **GitHub**: [github.com/Ghostkey316](https://github.com/Ghostkey316)

---

> *Morals over metrics. Privacy over surveillance. Flourishing over extraction.*

⚠️ **Alpha Software** — Vaultfire is under active development. Smart contracts have not been audited by a third party. Use at your own risk.
