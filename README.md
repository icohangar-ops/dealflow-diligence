# dealflow-diligence

**Deal Flow: NYC's First VC Hackathon** — Sat Oct 24, 2026, 9:00 AM–6:00 PM ET, Betaworks NYC.
**Track 2: Diligence. Underwrite a startup in an hour, not two weeks**

> **Status: pre-event scaffold only.** The organisers say *"On Saturday you only build. Everything a founder does before writing code happens this week."* This repo therefore holds only the plan, founder-brief template, interview notes template, a synthetic dataset (the track brief explicitly says to generate synthetic data before the event), and an empty package with a data-loading smoke test. **No product features have been built yet** — they get written on build day.

## Problem statement (verbatim from organisers)
VCs told us the three things that matter most in diligence: a startup's market signals, its comps, and the issues hiding in its financials and metrics. A first pass still takes an associate days of pulling data, rebuilding numbers from a messy data room and spotting what does not add up. Build a tool that takes a deck or data room and returns the market signals, the right comps and the red flags a partner needs before a second meeting.

**Who has this problem:** associates and principals at VC funds, angels doing diligence alone, accelerators screening hundreds of applicants.

**Data to start with:** public company filings on SEC EDGAR for comps, the Akta API from Wokelo, Crunchbase, and web search APIs such as You.com and Tavily. Bring a synthetic data room; never upload a real company's confidential data.

## Working idea (to validate in interviews)
Red-flag engine: deterministic checks (deck vs model mismatches, non-recurring 'ARR', burn vs hiring plan, hidden cohort churn) + first-draft memo where every claim cites its source.

## Interview questions (from organisers)
- What do you check first when you open a data room?
- Which red flag did you once miss and regret?
- How long does your first-pass memo take, and which part is the slowest?

## Prior work to reference
- [Live-Diligence](https://github.com/icohangar-ops/Live-Diligence) — EDGAR + Exa + LLM memo synthesis (reference only; code to be written on build day)
- [SEC-earnings-workbench](https://github.com/icohangar-ops/SEC-earnings-workbench) — fundamentals/diligence agent split (reference only; code to be written on build day)
- [finance-engines](https://github.com/icohangar-ops/finance-engines) — deterministic finance checks (reference only; code to be written on build day)
- [proof-of-assay](https://github.com/icohangar-ops/proof-of-assay) — deterministic tolerance checks + hash-chained receipt pattern (reference only; code to be written on build day)

## Planned architecture (to build Saturday)
ingest (public APIs / synthetic files) → deterministic checks/scoring → LLM explanation with citations → Streamlit one-workflow demo. Every output links to its source row/document.

## Saturday finalize checklist
- [ ] Founder brief filled in (`docs/FOUNDER_BRIEF.md`) with real interview evidence
- [ ] Market map filled in (`docs/MARKET_MAP.md`)
- [ ] Build the one demo workflow (core logic + tests)
- [ ] Streamlit UI for the demo
- [ ] Record 2-min demo / prep pitch (business + code are judged equally)
- [ ] Submit via the organisers' Saturday process (not yet announced)

## Demo plan
Drop the synthetic data room in, get red flags in <60s, each linked to the file/cell that triggered it, plus a 1-page memo.

## Run
```bash
pip install -e .[dev]
python -m dealflow_diligence            # prints synthetic dataset summary
pytest -q
```

## Data
`data/synthetic/` is **synthetic, fabricated data**. Never commit real confidential company, fund or LP documents.

MIT License.
