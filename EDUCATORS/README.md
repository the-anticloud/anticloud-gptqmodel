# Educators — GPTQMODEL

**Project:** GPTQMODEL  
**Category:** CHIP_QUANTIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `521f085c60b9a3e5c918cc4608cf31cbe540235d`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `04fc6f89b1e4c745c5e91941b60bdfbaeb09d0041357a86d4bf6d925f594113e`  
**Date:** October 2026

## Teaching with GPTQMODEL

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `04fc6f89b1e4c745c5e91941b60bdfbaeb09d0041357a86d4bf6d925f594113e` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
