# WFP Ethiopia – Targeting Verification Sampling App (Somali Region RAM)

**v3 FULL BUILD**
- Preserves **all original fields** in outputs.
- **Unique-only** sampling (no replacement); drops duplicate HHs by `HH_ID`.
- **Reallocates village shortfalls** within the same kebele to other selected villages (capacity-aware).
- Fixes NumPy dtype issue by using pandas-native label assignment for `Group`.
- Includes Excel & CSV-bundle downloads, guidance notes, and Dockerfile.

## Quick start
```bash
python -m venv .venv
. .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

## Deploy with Docker
```bash
docker build -t wfp-verification-sampling:v3 .
docker run -p 8501:8501 wfp-verification-sampling:v3
```
Open http://localhost:8501

## Inputs & mapping
Map: **kebele**, **village/EA/block**, **eligibility flag**, and optional **HH_ID** (if absent, the app creates one).

## Outputs
- `Summary_By_Kebele` (planned vs actual; shortfalls)
- `Village_Selection` (PPS picks + final per-village allocations)
- `Household_Samples_AllFields` (all input columns + sampling metadata)
- `Reserve_List_AllFields` (optional)
- `Run_Parameters`
