# ThermaGrid — 3-Minute Pitch Script

Use this as a talking outline, not a script to read word-for-word. Practice it twice out loud before tomorrow — timing matters more than wording.

## 0:00–0:25 — The Hook
> "Right now, some blocks in Delhi are running 6–7°C hotter than blocks a few kilometers away — same city, same day. That gap kills people during heatwaves, and it's completely fixable. The problem is planners don't know *which* block to fix, *what* to do to it, or *whether they can afford it*. ThermaGrid answers all three."

## 0:25–0:55 — The Problem (make it concrete)
- Urban heat islands aren't uniform — they're hyper-local (block by block).
- Cities have heat-mitigation budgets but no tool that turns satellite data into a prioritized, costed action list.
- Existing heat maps show *where* it's hot. None show *why*, *what to do about it*, or *what it costs*.

## 0:55–2:10 — Live Demo (this is the core of your score — go slowly)
1. **Open the Thermal Map** — "Here's Delhi, gridded into 625 zones from satellite-style vegetation, built-up, and reflectance indices." Point at a visibly red hotspot.
2. **Click a hotspot → show SHAP attribution** — "The model doesn't just say it's hot — it tells us *why*: this zone is hot mostly because of low vegetation and dark rooftops, not density." This is your differentiator — say the word "explainable" out loud.
3. **Drag the intervention sliders** (greening / cool roofs / de-paving) — show the **before/after heatmap** updating and the predicted °C drop.
4. **Show the budget + water constraint panel** — "Every plan is checked against a real budget and a daily water limit — because a tree-planting plan that ignores water isn't a plan, it's a wish."
5. **Switch to ROI Ranking** — "Instead of guessing, planners see which zones give the most cooling per rupee spent."
6. **Open the AI Copilot / Policy Brief** — ask it a question live, then generate the executive brief. "This turns a technical simulation into something a city council can actually vote on."

## 2:10–2:40 — Why This Wins (technical credibility)
- XGBoost regression trained on physics-informed synthetic indices, explained per-zone with SHAP (not a black box).
- Model reports its own R², RMSE, and stated limitations — built for planner trust, not just demo polish.
- Every output is labeled as a modelled estimate / candidate area — honest about uncertainty.

## 2:40–3:00 — Impact + Close
> "Heat is the deadliest form of climate disaster, and it's the one we can solve with trees and paint, if we know where to spend. ThermaGrid is the difference between a city that reacts to heatwaves and one that plans ahead of them."

---

## Anticipated judge questions (have answers ready)

**"Is this real satellite data?"**
→ "The current grid is synthetically generated from physics-informed equations calibrated to realistic NDVI/NDBI/albedo/LST relationships — built this way so we could demo the full pipeline in a hackathon timeframe. The architecture is designed to swap in real Landsat/Sentinel data via Google Earth Engine as the next step — the model, SHAP, costing, and ROI ranking logic don't change."

**"How accurate is the cooling prediction?"**
→ Point to the model card: R², RMSE and uncertainty bounds are surfaced in the UI itself, plus explicit stated assumptions (clear summer afternoon, static microclimate, tree-maturation timeline).

**"What happens without an OpenAI key?"**
→ "The copilot and policy brief both have a rule-based fallback, so the core product never breaks — GPT-4o-mini just makes the responses richer when a key is present."

**"How would a city actually deploy this?"**
→ Real satellite ingestion → per-ward calibration of cost assumptions with local vendors → GIS export for planning departments (see Roadmap in README).

## Before you present — quick checklist
- [ ] Backend running (`uvicorn main:app --reload --port 8000`) *before* you start talking
- [ ] Frontend running and already loaded to the dashboard (not the homepage) so you don't fumble clicks live
- [ ] Pick one zone in advance that has a clean, dramatic before/after story — don't hunt for it live
- [ ] Have a fallback: a screen recording of the working demo in case venue wifi/localhost has issues
- [ ] Know your R²/RMSE numbers off the top of your head — judges love when you don't have to look
