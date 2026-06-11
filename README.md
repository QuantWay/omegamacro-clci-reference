# OmegaMacro CLCI — Public Reference

This repository is the public reference for the OmegaMacro Composite Late-Cycle
Indicator (CLCI). It documents, in prose, what the indicator is, how its published
signal is constructed in concept, and where to find the artefacts that let a
reader verify the firm's track record. It deliberately does **not** contain code
that reproduces the indicator's published output. The reasons for that are
explained below, and they are a feature of the design, not an omission.

## What the CLCI is

The CLCI is a weekly reading, on a 0–100 scale, of how much late-cycle pressure
has accumulated in the economic and financial system. It is built from seven
thematic blocks of macro-financial data — Yield Curve, Credit, Labour, Liquidity,
Earnings Revisions, Valuation, and Breadth — each measuring a distinct channel
through which late-cycle pressure manifests. The blocks are combined into a single
composite, and the composite is read against the indicator's own accumulated
history to produce the published signal.

The full methodology is described on the methodology page
(omegamacro.com/methodology) and in the SSRN methodology paper, linked below. This
README summarises the parts that bear on reproducibility and verification.

## The published signal, in concept

The published signal is derived from the composite by reading it as a **percentile
against the indicator's own accumulated history** — that is, by expressing how
unusual the current reading is relative to the history the indicator has seen.
That reading is mapped to five descriptive bands — **subdued**, **normal**,
**elevated**, **high**, and **very high** — and accompanied by a direction note
indicating whether pressure is rising, easing, or steady. A persistence treatment
stabilises the published reading so that a transient movement does not register as
a regime change.

These bands are a **description of a measurement, not a categorical prediction**.
"Elevated" means current pressure is high relative to history; it does not assert
that a recession is imminent. This is the same "probabilities, not predictions"
discipline the firm applies throughout. The descriptive bands are a communication
convention, set in advance and never tuned to fit any historical episode; the
specific cut-points that separate one band from the next are part of the
proprietary computation described below, not published numbers.

## What this repository does not contain, and why

This repository does not contain code that reproduces the published regime labels
from the composite series. The exact method that converts the composite into the
published reading — the computation behind the percentile-against-history bands —
is proprietary and is not published in any form, here or elsewhere.

This is a deliberate decision. The composite output series is published in full in
the Zenodo replication pack (linked below), so that the firm's track record can be
independently verified. Publishing, in addition, the exact code that maps that
composite to the published labels would hand a competitor the complete output half
of the system — and the firm's calibration work is the asset that makes it a going
concern. The architecture is open; the implementation is the firm's own. This is
the same architecture-versus-implementation boundary that comparable systematic
research operates within.

Crucially, withholding the reproduction code costs a reader nothing in terms of
trust, because the credibility of the track record does not rest on it. It rests
on two independent, verifiable foundations described next.

## How the track record is verifiable without reproduction code

**A dated track record.** Every Quarterly Turning Point Report, with the regime
call it made and what subsequently happened, is recorded in a dated, chronological
table on the About page. The record is published as events unfold, not
reconstructed afterward, and documented misses are logged openly alongside the
calls.

**A cryptographic pre-commitment.** Each methodology version's parameter file is
hashed (SHA-256), and the hash is deposited publicly with the corresponding
replication pack. This proves that the parameters which produced a published
series existed before the series was published — that the firm did not adjust its
method after seeing outcomes. Combined with a standing commitment never to change
a parameter retroactively, this lets a reader confirm the integrity of the record
without needing to re-run any code.

A reader who can see what was called, when, against what subsequently happened, and
can verify the parameters were fixed in advance, has strong evidence of the firm's
honesty — which is what reproduction code would have been asked to provide, at the
cost of the firm's calibration work.

## Links

- **Methodology page:** omegamacro.com/methodology
- **SSRN methodology paper:** `https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6920398`
- **Zenodo replication pack** (the published composite series, the published
  regime classification series, the block-level series, and the parameter-file
  hash): https://doi.org/10.5281/zenodo.20632043
- **Dated track record and documented-misses log:** omegamacro.com/track-record

## License

Released under the MIT License (see `LICENSE`). The license covers this
documentation; it does not grant any rights in the proprietary methodology or
implementation, which are not distributed here.
