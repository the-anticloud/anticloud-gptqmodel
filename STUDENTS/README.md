# Students — GPTQMODEL

**Project:** GPTQMODEL  
**Category:** CHIP_QUANTIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `521f085c60b9a3e5c918cc4608cf31cbe540235d`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `04fc6f89b1e4c745c5e91941b60bdfbaeb09d0041357a86d4bf6d925f594113e`  
**Date:** October 2026

## What this project gives you

A complete worked example of offline-first packaging with a cryptographic audit
chain: source pinned at `521f085c60b9a3e5c918cc4608cf31cbe540235d`, a 16-check assurance suite, an evidence register
with per-check hashes, and an AIOSS ledger chain ending at `04fc6f89b1e4c745c5e91941b60bdfbaeb09d0041357a86d4bf6d925f594113e`.

## Learn by verifying

```
python tools/run_bench.py --out BENCH.json
```

Then take any row from `ISOLATED_LAB_RESULTS/03_Result_Register.md`, recompute
the SHA3-256 of its evidence file, and confirm it matches. If it does not match,
the record has been altered — that is the whole point of the chain.

## Licence

Apache 2.0 terms apply to study and teaching use.
