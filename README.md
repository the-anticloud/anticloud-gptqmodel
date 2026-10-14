# GPTQMODEL

![license](https://img.shields.io/badge/license-license-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-chip_quantization-lightgrey)

> Anticloud-hardened packaging of the upstream project `GPTQMODEL` in category **CHIP QUANTIZATION**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** CHIP QUANTIZATION · **Upstream:** https://github.com/houmo-ai/postmo-gptqmodel · **Upstream pin:** `521f085c60b9a3e5c918cc4608cf31cbe540235d` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

<!-- SPDX-FileCopyrightText: 2024-2026 ModelCloud.ai -->
<!-- SPDX-FileCopyrightText: 2024-2026 qubitium@modelcloud.ai -->
<!-- SPDX-License-Identifier: Apache-2.0 -->
<!-- Contact: qubitium@modelcloud.ai, x.com/qubitium -->

<p align=center>
<div align=center>
<img src="https://github.com/user-attachments/assets/ab70eb1e-06e7-4dc9-83e5-bd562e1a78b2" width=500>
</div>
<h1 align="center">GPT-QModel ⚡</h1>
</p>
<p align="center"><strong>An extensible platform for LLM quantization, validation, and deployment.</strong><br>GPTQ, AWQ, ParoQuant, GGUF, FP8, EXL3, QQQ, and more—across NVIDIA CUDA, AMD ROCm, Huawei Ascend, Intel XPU, and CPU, with Transformers, vLLM, and SGLang.</p>
<p align="center">
    <a href="https://github.com/ModelCloud/GPTQModel/releases" style="text-decoration:none;"><img alt="GitHub release" src="https://img.shields.io/github/release/ModelCloud/GPTQModel.svg"></a>
    <a href="https://pypi.org/project/gptqmodel/" style="text-decoration:none;"><img alt="PyPI - Version" src="https://img.shields.io/pypi/v/gptqmodel"></a>
    <a href="https://pepy.tech/projects/gptqmodel" style="text-decoration:none;"><img src="https://static.pepy.tech/badge/gptqmodel" alt="PyPI Downloads"></a>
    <a href="https://github.com/ModelCloud/GPTQModel/blob/main/LICENSE"><img src="https://img.shields.io/pypi/l/gptqmodel"></a>
    <a href="https://huggingface.co/modelcloud/"><img src="https://img.shields.io/badge/🤗%20Hugging%20Face-ModelCloud-%23ff8811.svg"></a>
    <a href="https://huggingface.co/models?search=gptq">
        <img alt="Huggingface - Models" src="https://img.shields.io/badge/🤗_6.7K_gptq_models-8A2BE2">
    </a>
    <a href="https://huggingface.co/models?search=awq">
        <img alt="Huggingface - Models" src="https://img.shields.io/badge/🤗_8.2K_awq_models-8A2BE2">
    </a>
</p>

## Latest News 🗞️🚀

* 09/30/2026 7.6.0-dev `main`: ✨ Added `smolvlm` and `granitemoe` quantization support.
* 09/24/2026 7.6.0-dev `main`: ✨ Added `intervl` quantization support.
* 09/23/2026 7.6.0-dev `main`: ✨ Added `exaone4_5`, `qwen3_vl_moe` and `olmoe` quantization support.
* 09/16/2026 7.6.0-dev `main`: ✨ Added `zdtaichu5_0` quantization support.
* 09/16/2026 7.6.0-dev `main`: ✨ Added `agnes` quantization support.
* 09/15/2026 [7.5.0](https://github.com/ModelCloud/GPTQModel/releases/tag/v7.5.0): ✨ Added K2 Horizon, Qwen-Drive, Nanbeige, and Diffusion Gemma quantization support. Improved GPTQ/AWQ/ParoQuant reliability with device-aware kernel selection, safer CUDA dispatch and empty-input handling, partial packing-word support, correct calibration masks, model-specific Paro layer replay, and hardened Machete runtime caching. Loading and saving now validate GPTQ `qweight` and offload metadata, while InternVL image preprocessing keeps `torchvision` optional. Quantization finalization is faster and startup version reporting is more accurate.
* 09/07/2026 [7.4.0](https://github.com/ModelCloud/GPTQModel/releases/tag/v7.4.0): 🎉 Added resumable quantization checkpoints, shared-input Hessian deduplication, `lm_head` and embedding requantization, and updated native GGUF support. Added GLM-5.3-Flash, Apertus 1.5, and XHToken `ouro` / `spark2_5` quantization support, plus quantization, JIT cache, and Triton compatibility fixes.
* 08/31/2026 [7.3.6](https://github.com/ModelCloud/GPTQModel/releases/tag/v7.3.6): ✨ Added HunyuanOCR, NVIDIA LocateAnything-3B, and Qwen3.8-Flash-Next quantization support. Added tile-misaligned GPTQ/AWQ Marlin support, reduced QQQ packing memory, and improved JIT extension cache reuse.
* 08/25/2026 [7.3.5](https://github.com/ModelCloud/GPTQModel/releases/tag/v7.3.5): ✨ Added `lm_head` and embedding quantization lifecycle support; Unlimited-OCR, DeepSeek V3.2, Mage-VL, Muse Glimmer, OLMo 3, and SmolLM3 model support.
* 08/19/2026 [7.3.4](https://github.com/ModelCloud/GPTQModel/releases/tag/v7.3.4): 🚀🔥⚡ Added the `Swordfish` Blackwell GPTQ/AWQ kernel, planar GPTQ checkpoint formats, native MPS quantization, and Cohere Compass / A.X-K2 model support, with quantization performance and reliability improvements.
Older releases and development notes: [changelog archive](docs/changelog/archive.md).

## Prism Bonsai GGUF compatibility 📝

GPT-QModel loads Prism/Bonsai GGUF checkpoints through its native GGUF loading path and internal GGUF runtime shim. No external `gguf` PyPI package is required.

```py
from gptqmodel import GPTQModel

model = GPTQModel.load("prism-ml/Bonsai-1.7B-gguf")
# or: model = GPTQModel.load("prism-ml/Bonsai-1.7B-gguf", profile="low_memory")

tokens = model.generate(
    "Who wrote Romeo and Juliet?",
    max_new_tokens=128,
)[0]

print(model.tokenizer.decode(tokens, skip_special_tokens=True))
```

## A unified quantization platform

GPT-QModel provides a consistent API for calibration, quantization, quality evaluation, model conversion, and accelerated inference. It supports GPTQ, AWQ, ParoQuant, QQQ, GGUF, FP8, EXL3, GPTAQ, EoRA, GAR, and FOEM across supported hardware and runtime integrations.

Its method, format, backend, and kernel layers are modular: method-specific controls remain available where needed, while implementations share the same model lifecycle. This architecture supports mixed and model-specific quantization workflows today and provides a clear integration path for additional methods, formats, kernels, and accelerators.

## Quantization Support 🛠️

Every quantization method shares a common lifecycle—calibrate, quantize, validate, save, load, and serve—while retaining method-specific controls where they matter. New methods and kernels plug into that lifecycle instead of creating another disconnected toolchain.

| Feature      | GPT-QModel | Transformers | vLLM | SGLang | Lora Training |
|---------------------------|------------|---|---|---|---------------|
| GPTQ                      | ✅          | ✅ | ✅ | ✅ | ✅             | 
| AWQ                       | ✅          | ✅ | ✅ | ✅ | ✅             |
| ParoQuant                 | ✅          | x | x | x | ✅

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Python** (manifests: pyproject.toml, requirements.txt; scanned in UPSTREAM_CLONE)
- Top-level source layout: `format/`, `gptqmodel/`, `gptqmodel_ext/`, `hw/`, `licenses/`, `optimize/`, `scripts/`, `tests/`
- Snapshot size: **1393 files**, **297356 lines of code** (measured; see Benchmarks)
- Primary languages: `.py` (1159), `.cuh` (73), `.cu` (46), `.h` (27), `.md` (20), `.cpp` (16)
- Upstream commit pinned for this packaging: `521f085c60b9a3e5c918cc4608cf31cbe540235d`

---

## Installation

MLX-LM checkpoint:

```bash
pip install 'gptqmodel[mlx]'
```

```python
from gptqmodel import GPTQModel

GPTQModel.quantize_mlx(
    "Qwen/Qwen3-0.6B",
    "./qwen3-mlx-gptq",
    method="gptq",  # or "awq"
    bits=4,
    group_size=64,
    num_samples=128,
)
```

GPTQ uses MLX for calibration and weight updates, with one fused Metal dispatch
per weight group. MLX currently performs the Cholesky factorization on its CPU
stream. AWQ uses MLX-LM's native scale and clip search. The output uses MLX-LM's
quantized model format and can be loaded with `mlx_lm.load`.
Pass an MLX token array as `calibration_data` to use your own calibration set.

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

* 08/19/2026 [7.3.4](https://github.com/ModelCloud/GPTQModel/releases/tag/v7.3.4): 🚀🔥⚡ Added the `Swordfish` Blackwell GPTQ/AWQ kernel, planar GPTQ checkpoint formats, native MPS quantization, and Cohere Compass / A.X-K2 model support, with quantization performance and reliability improvements.
Older releases and development notes: [changelog archive](docs/changelog/archive.md).

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

Its method, format, backend, and kernel layers are modular: method-specific controls remain available where needed, while implementations share the same model lifecycle. This architecture supports mixed and model-specific quantization workflows today and provides a clear integration path for additional methods, formats, kernels, and accelerators.

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Python |
| Manifests detected | pyproject.toml, requirements.txt |
| Files in snapshot | 1393 |
| Lines of code | 297356 |
| Dependency references | 0 |
| Upstream license | Apache-2.0 |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

* 🚀 Intel Torch 2.8 fused kernel support for XPU [`Arc` + `Datacenter Max`] and CPU [`avx`, `amx`].
* 🚀 Python 3.13.3t (free-threading, GIL disabled) support for multi-GPU accelerated quantization for MoE models and multi-core CPU boost for packing.
* ✨ Asymmetric `Sym=False` support. 
* ✨ `lm_head` module quant inference support for further VRAM reduction.
* 🚀 [Microsoft/BITBLAS](https://github.com/microsoft/BitBLAS) optimized tile based inference.
* 💯 CI unit-test coverage for all supported models and kernels including post-quantization quality regression.

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `GPTQMODEL` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: Apache-2.0** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
# SPDX-FileCopyrightText: 2024-2025 ModelCloud.ai
# SPDX-FileCopyrightText: 2024-2025 qubitium@modelcloud.ai
# SPDX-License-Identifier: Apache-2.0
# Contact: qubitium@modelcloud.ai, x.com/qubitium

                                Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original Apache-2.0 terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `Apache-2.0` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `GPTQMODEL` (category: CHIP QUANTIZATION)
- **Upstream URL:** https://github.com/houmo-ai/postmo-gptqmodel
- **Pinned commit (SHA):** `521f085c60b9a3e5c918cc4608cf31cbe540235d`
- **Branch:** release_xh2_v1.5.0
- **Pin provenance:** GitHub API commits/release_xh2_v1.5.0. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`1275767b5e3591d4687d17c8a08eadd371eb57db9a4f6fbc2e458255e5d44642`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

