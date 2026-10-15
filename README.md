# AI Visibility Index: which agencies do ChatGPT, Perplexity and Gemini recommend?

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23385485.svg)](https://doi.org/10.5281/zenodo.23385485)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](LICENSE)

Open dataset by [Grovia Digital](https://www.grovia-digital.com/en/) (Dubai). We ask
ChatGPT, Perplexity and Gemini the questions buyers ask when they look for an agency
for AI search visibility (generative engine optimization, GEO), in German and English,
and record which providers the assistants name and which sources they cite.

The same method runs every two weeks. Each measurement is published here.

## What is in the data

| Measurement | Date | Scope | Measurements |
|---|---|---|---|
| Baseline | 2–9 Sep 2026 | 35 prompts, 3 platforms, 5 runs | 525 |
| Pulse P1 | 24 Sep 2026 | 10 prompts (block A) + 4 GCC prompts (block B), 3 runs | 114 |
| Pulse P2 | 8 Oct 2026 | 10 prompts (block A), 3 runs | 90 |

Baseline in numbers: 596 firms and 97 software tools named, 3,335 source rows from
1,044 domains. The most-named provider reached 2.2 % of all mentions.

Grovia Digital measures itself with the same method: 0 mentions in the 525 baseline
answers; in Pulse P2, Perplexity named Grovia Digital on one buyer question in 2 of 3
runs. ChatGPT and Gemini did not name it (0 of 60).

## Files

All files are UTF-8, semicolon-separated.

`data/baseline-2026-09-10/`

| File | Content |
|---|---|
| `..._prompts.csv` | prompt ID, language, category, exact wording (frozen) |
| `..._measurements.csv` | one row per answer: date, time (CEST where recorded), platform, model, run, location/VPN, providers and tools named, whether sources were captured |
| `..._sources.csv` | one row per cited source: measurement ID, domain, URL, source type, position |
| `..._providers.csv` | providers in alphabetical order with the number of measurements naming them |
| `..._limitations.csv` | every declared limitation of the measurement |

`data/pulses/`

| File | Content |
|---|---|
| `..._P1_measurements.csv`, `..._P2_measurements.csv` | same columns as the baseline plus `pulse`, `block`, `grovia_rank`, `map`, `paid_placement` |
| `..._P1_sources.csv`, `..._P2_sources.csv` | cited sources per measurement |

## Method

- Frozen prompt set, exact wording, new empty chat per measurement, web search on,
  memory and personalisation off.
- VPN exit Frankfurt. Times in CEST.
- A provider counts once per answer. Spelling variants of the same provider are
  merged. Names of individual persons are replaced by "Individual consultant (name
  removed)". Software tools are counted separately from agencies.
- Pulses (3 runs) are compared only with runs 1–3 of the baseline, never with the
  five-run figures.
- Gemini shows sources as display names without URL, so domain frequencies should be
  read per platform.
- Mention frequency is not a statement about quality.

All limitations are listed in `..._limitations.csv`. Changes between versions are in
`CHANGELOG.md`.

## Use and citation

Licence: [CC BY 4.0](LICENSE). You may use, share and adapt the data, including
commercially, with attribution:

> Grovia Digital (Grovia Management Consultancy L.L.C), AI Visibility Index, 2026.
> Zenodo. https://doi.org/10.5281/zenodo.23385485

The DOI above always resolves to the latest version. Each release has its own
version DOI on Zenodo (version 2026-10-08: https://doi.org/10.5281/zenodo.23385486).
A machine-readable citation is in `CITATION.cff` (GitHub shows it as "Cite this
repository").

## Links

- Live index with the measurement diary: https://www.grovia-digital.com/en/geo-visibility-index/
- Case: how Perplexity started naming Grovia Digital: https://www.grovia-digital.com/en/case-studies/grovia-named-by-perplexity/
- Grovia Digital: https://www.grovia-digital.com/en/
