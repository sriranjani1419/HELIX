# KARUNX LABS — HELIX
### Space Biology Intelligence Platform | NASA Space Apps Challenge 2026

**HELIX** is a computational systems biology platform developed by **KARUNX LABS** to investigate spaceflight-associated human immune-system dysregulation across molecular and physiological levels.

---

## Scientific Architecture

1. **NASA OSDR / GeneLab Data Provenance Engine (`Stage 1–2`)**
   - Integrates verified human spaceflight immune studies (`OSD-570`, `OSD-575`, `OSD-569`, `OSD-53`) via the NASA OSDR REST API with strict provenance tagging (`NASA_OSDR_API_LIVE` vs. `NASA_OSDR_CURATED_CATALOG`).
   - Uses pathway-level signature aggregation (`IL6`, `NFKBIA`, `IL2RA`, `GZMB`, `PRF1`, `IFNG`) to prevent high-dimensional overfitting on small astronaut cohorts ($N=4$ to $N=12$).

2. **Mechanistic Immune System ODE Engine (`Stage 3–4 `)**
   - Integrates coupled ordinary differential equations (`SciPy RK45`) modeling T-cell TCR/IL-2 activation $T(t)$, NK-cell cytolytic activity $K(t)$, and IL-6/NF-$\kappa$B inflammatory tone $I(t)$ under microgravity and ionizing radiation stress.

3. **Group-Validated Hybrid Residual Machine Learning (`Stage 5–8`)**
   - Implements $Y_{\text{hybrid}}(t) = Y_{\text{mechanistic}}(t) + f_\theta(X, t)$ using L1/L2-regularized `ElasticNet` and shallow `XGBoost` evaluated under subject-blocked `GroupKFold` cross-validation with bootstrap 95% confidence bands.

---

## Local Execution (macOS / Apple Silicon)

### 1. Start the FastAPI Scientific Backend
```bash
source backend/.venv/bin/activate
uvicorn app.main:app --app-dir backend --host 127.0.0.1 --port 8000 --reload
