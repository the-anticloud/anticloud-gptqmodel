# Ethics — GPTQMODEL

**Project:** GPTQMODEL  
**Category:** CHIP_QUANTIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `521f085c60b9a3e5c918cc4608cf31cbe540235d`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `04fc6f89b1e4c745c5e91941b60bdfbaeb09d0041357a86d4bf6d925f594113e`  
**Date:** October 2026

## Position

GPTQMODEL is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
