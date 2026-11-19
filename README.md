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
| Pulse P3 | 22 Oct 2026 | 10 prompts (block A) + 4 GCC prompts (block B, ChatGPT and Perplexity), 3 runs | 114 |
| Pulse P4 | 5 Nov 2026 | 10 prompts (block A), 3 runs | 90 |
| Pulse P5 | 19 Nov 2026 | 10 prompts (block A) + 4 GCC prompts (block B, ChatGPT and Perplexity), 3 runs | 114 |

Baseline in numbers: 596 firms and 97 software tools named, 3,335 source rows from
1,044 domains. The most-named provider reached 2.2 % of all mentions.

Grovia Digital measures itself with the same method: 0 mentions in the 525 baseline
answers. In Pulse P2 (8 Oct 2026), Perplexity named Grovia Digital on one buyer question
in 2 of 3 runs. In Pulse P3 (22 Oct 2026), ChatGPT named it in 6 of 12 measurements on
the GCC prompts (block B), on "ai visibility agency uae" in 3 of 3 runs. In P3 block A
(90 measurements) and on Perplexity in block B (12) it was not named. In Pulse P4 (5 Nov
2026), Perplexity named Grovia Digital first on E01 in run 1 (1 of 90 measurements) and cited
a Grovia page in 5 answers, all on Perplexity. In Pulse P5 (19 Nov 2026), Grovia Digital was
named in 12 of 114 measurements: 4 of 90 in block A and 8 of 24 on the GCC prompts (block B).
Perplexity accounts for 11 of the 12 mentions, ChatGPT for 1. Two questions were named in 3 of
3 runs, both on Perplexity (E14 and E20). A Grovia page or profile was listed as a source in 27
measurements. Gemini has not named it in any measurement so far.

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
| `..._P1_measurements.csv` to `..._P5_measurements.csv` | same columns as the baseline plus `pulse`, `block`, `grovia_rank`, `map`, `paid_placement`; from P5 also `sources_status` |
| `..._P1_sources.csv` to `..._P5_sources.csv` | cited sources per measurement (P2 to P4: Perplexity only; P5: ChatGPT, Gemini and Perplexity) |

## Method

- Frozen prompt set, exact wording, new empty chat per measurement, web search on,
  memory and personalisation off.
- VPN exit Frankfurt. Times in CEST; from P4 (5 Nov 2026) in CET, winter time. The column
  keeps the name `time_cest` so the schema stays the same across files.
- A provider counts once per answer. Spelling variants of the same provider are
  merged. Names of individual persons are replaced by "Individual consultant (name
  removed)". Software tools are counted separately from agencies.
- Pulses (3 runs) are compared only with runs 1–3 of the baseline, never with the
  five-run figures.
- Gemini shows sources as display names without URL, so domain frequencies should be
  read per platform.
- Mention frequency is not a statement about quality.

## Source coverage

Source mixes differ by platform, so read them per platform and language. Pooled shares mostly
describe Perplexity, which contributes 80 % of all baseline source rows (2,683 of 3,335).

Baseline (525 answers):

| Platform | Language | Answers | Sources captured | Marked "no" | Not recorded | Source rows | Most frequent source type |
|---|---|---|---|---|---|---|---|
| ChatGPT | DE | 75 | 20 | 52 | 3 | 82 | Company website 88 % |
| ChatGPT | EN | 100 | 24 | 67 | 9 | 117 | Company website 91 % |
| Gemini | DE | 75 | 60 | 11 | 4 | 198 | Company website 84 % |
| Gemini | EN | 100 | 80 | 1 | 19 | 255 | Company website 59 % |
| Perplexity | DE | 75 | 75 | 0 | 0 | 1,104 | Company website 59 %, comparison list 14 % |
| Perplexity | EN | 100 | 100 | 0 | 0 | 1,579 | Company website 36 %, comparison list 30 % |

In the baseline, "no" does not separate answers that displayed no source from answers whose
sources were not captured. The two cases cannot be told apart afterwards. Two answers marked
"no" have source rows (E01-CHA-4: 1 row, E07-GEM-2: 6 rows).

Pulse P5 (114 answers). From P5 on, every answer carries `sources_status`: `shown` (at least one
source displayed and captured), `none shown` (the answer displayed no source) or `not captured`
(sources were visible or unclear and were not recorded).

| Platform | Language | Answers | Shown | None shown | Not captured | Source rows | Most frequent source types |
|---|---|---|---|---|---|---|---|
| ChatGPT | DE | 18 | 15 | 0 | 3 | 295 | Comparison list 61 %, company website 22 % |
| ChatGPT | EN | 24 | 19 | 0 | 5 | 313 | Comparison list 61 %, company website 31 % |
| Gemini | DE | 18 | 18 | 0 | 0 | 97 | Company website 76 %, comparison list 9 % |
| Gemini | EN | 12 | 11 | 1 | 0 | 43 | Company website 67 %, trade media 9 % |
| Perplexity | DE | 18 | 18 | 0 | 0 | 294 | Company website 51 %, comparison list 25 % |
| Perplexity | EN | 24 | 24 | 0 | 0 | 376 | Company website 48 %, press release portal 20 % |

P5 is the first pulse with ChatGPT and Gemini sources. ChatGPT's source panel and Gemini's
source chips show domain and title without a URL, so the `url` field is empty in 748 of 1,418
P5 source rows. For Gemini only the chips were recorded. Baseline and P5 differ in how ChatGPT
sources were captured (P5 includes the source panel), so the two ChatGPT rows are not directly
comparable.

All limitations are listed in `..._limitations.csv`. Changes between versions are in
`CHANGELOG.md`.

## Use and citation

Licence: [CC BY 4.0](LICENSE). You may use, share and adapt the data, including
commercially, with attribution:

> Grovia Digital (Grovia Management Consultancy L.L.C), AI Visibility Index, 2026.
> Zenodo. https://doi.org/10.5281/zenodo.23385485

The DOI above always resolves to the latest version. Each release has its own
version DOI on Zenodo (version 2026-10-08: https://doi.org/10.5281/zenodo.23385486,
version 2026-10-22: https://doi.org/10.5281/zenodo.23567898,
version 2026-11-05: https://doi.org/10.5281/zenodo.24031116,
version 2026-11-19: https://doi.org/10.5281/zenodo.24369418).
A machine-readable citation is in `CITATION.cff` (GitHub shows it as "Cite this
repository").

## Links

- Live index with the measurement diary: https://www.grovia-digital.com/en/geo-visibility-index/
- Case: how Perplexity started naming Grovia Digital: https://www.grovia-digital.com/en/case-studies/grovia-named-by-perplexity/
- Grovia Digital: https://www.grovia-digital.com/en/
