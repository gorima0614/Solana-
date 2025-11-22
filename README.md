anchor-program/               # On-chain Anchor program (smart contract)
backend-oracle-service/       # Rust backend oracle clients & aggregation services
migrations/                   # Database schema and migration scripts
tests/                       # Integration and unit tests
.env.example                  # Example environment configuration
scripts/                      # Utility scripts (deploy, run backend, migrate DB)
README.md                     # This documentation

Perpetual Futures DEX Oracle Stack
Overview
This repository contains a complete reference implementation for a high-performance, secure, and scalable perpetual futures decentralized exchange (DEX) oracle system on Solana. It integrates on-chain Anchor smart contracts with off-chain Rust-based oracle clients and backend services supporting multiple oracle feeds (Pyth, Switchboard) and real-time price aggregation.

Key features:

Anchor program implementing trusted oracle price feed accounts with validation and security.

Rust backend services for reliable off-chain data ingestion, multi-source price aggregation, caching with Redis, and serving REST API and WebSocket streams.

PostgreSQL database schema and migration scripts for price history and oracle health metrics storage.

Test suite covering core contract logic, backend modules, and integration scenarios.

Modular architecture designed for extension and production readiness.

Prerequisites
Solana CLI (latest version): https://docs.solana.com/cli/install-solana-cli-tools

Rust toolchain: https://rustup.rs/

Anchor framework: https://www.anchor-lang.com/docs/installation

PostgreSQL database

Redis server

Node.js and npm (for Anchor TypeScript clients and test utilities)

Price Flow:
Pyth Feed ──┐
            ├─→ [Price Aggregator] → [Consensus Price] → Redis Cache → API
Switchboard─┘                                              ↓
                                                      PostgreSQL


