---
title: Factory WIP & MES Integration with RFID — From Shipped Tooling Management Toward WIP Tracking
description: WIP tracking and real-time MES integration are high-value targets for manufacturing. AssetaGuard ships tooling check-out, finder mode, and asset counts today; gate readers, MES integration, and inspection SOPs are on the roadmap and open to pilot co-build.
date: 2026-05-09
industry: manufacturing
tags: [manufacturing, WIP, MES, RFID, application exploration, co-build]
author: AssetaGuard team
readingMinutes: 8
---

> ℹ️ **About this article**: This is an **application exploration** piece. The "top of the pyramid" for manufacturing RFID is WIP (work-in-process) flow tracking + real-time MES integration. **AssetaGuard ships today** the tooling check-out, finder mode, monthly asset counts, and supply ledger; **gate readers + auto-report-out, real-time MES integration, equipment inspection SOPs, maintenance reminders** are on the roadmap and need to be co-built with manufacturing pilot customers. If your factory is evaluating this path, please get in touch.

## TL;DR

The reason MES work-order progress data drifts is that **inter-station flow is reported by humans**. In theory, RFID gate readers + bidirectional MES integration can lift progress accuracy from 70% to 99% — but that solution has high prerequisites on **process route stability, MES API availability, and shop-floor metal environments**. AssetaGuard's strategy is to **ship the "tooling check-out + asset counts + supply ledger" layer first** so customers see ROI from RFID immediately, while co-building the full WIP / MES integration with a small number of manufacturing pilot customers.

## I. The manufacturing capability pyramid

If you map RFID capabilities by "value × difficulty," it looks like this:

```
            ┌──────────────────────────────────┐
            │  Top (high value, high difficulty)│
            │  WIP flow + MES integration       │  🛣️ Roadmap
            │  Inspection SOP + work orders     │  🛣️ Roadmap
            │  Maintenance & calibration cycles │  🛣️ Roadmap
            ├──────────────────────────────────┤
            │  Mid (high value, medium difficulty)│
            │  Tooling and fixture check-out    │  ✅ Shipped
            │  Equipment / tooling finder mode  │  ✅ Shipped
            │  Monthly full-asset count         │  ✅ Shipped
            ├──────────────────────────────────┤
            │  Bottom (practical, low difficulty)│
            │  Asset receiving + lifecycle log  │  ✅ Shipped
            │  Supply ledger                    │  ✅ Shipped
            └──────────────────────────────────┘
```

**The bottom and middle layers alone deliver visible ROI in 3–6 months** — tool find time from 30 minutes to 30 seconds, monthly shrinkage from 5% to 0.3%. The top layer is the "RFID-in-manufacturing vision for the next 3 years," but it needs customer co-build.

## II. Why MES progress data drifts

Mainstream MES work-order progress comes from workers scanning a work-order barcode at the station and "reporting out." The problems:

- The actual flow takes an hour, the report-out takes 30 seconds — workers **batch the reports**.
- Reports are easy to edit, no one audits them.
- Items get misplaced across stations — the system doesn't know until downstream reports a missing piece.

**Result: the "WIP distribution" the MES sees is not what's actually on the floor**, and scheduling runs on intuition. This is a universal manufacturing problem, but the fix isn't "add another scan action" — it's making the flow **automatic to record**.

## III. Technical possibility — RFID + MES (exploration direction)

For full WIP tracking, the architecture would need:

### 3.1 Tag the pallet, not the part

Parts may go through grinding, welding, or heat treatment — **tags on parts get destroyed**. So tag the **pallet / tote**:
- One pallet corresponds to a batch of parts (10–100 pieces)
- Pallet RFID tag has a long lifecycle
- Parts ride the pallet without their own tags

### 3.2 Workstation gate readers (roadmap)

A gate reader (~1 m wide, ¥15K–¥30K each) at each station entrance / exit:
- Pallet enters = process started (auto-report-out)
- Pallet exits = process completed
- Data pushed to MES in 0.5 seconds

**AssetaGuard does not ship this hardware + software solution today** — it requires per-customer station layout design and integration.

### 3.3 Real-time bidirectional MES integration (roadmap)

Requires the MES to expose:
- Pull current work-order routings
- Push process progress write-back
- Exception event callbacks

AssetaGuard today integrates with ERPs (Yonyou / Kingdee / custom) via standard REST API + CSV import/export for book-physical reconciliation. **Real-time MES integration is not in the current product scope** and requires project-based custom work.

## IV. Prerequisites that actually matter

If your factory is evaluating the full WIP / MES + RFID solution, evaluate these first:

| Prerequisite | Status | Notes |
| --- | --- | --- |
| Process routing stable for 3+ months | ⚠️ Critical | Gate-reader placements move when routings change — frequent line changes don't fit |
| MES has a usable interface | ⚠️ Critical | Standard MES (QAD / Plex / SAP DMC) has APIs; custom MES needs 2–4 weeks of joint integration |
| Shop floor supports RFID | ⚠️ Critical | Metal-dense / high-temp / EM-strong areas need specialized tags + on-site testing |
| Pilot line selection | Recommended | Start with 5 stations → one line → full plant |
| Worker cooperation mechanism | Recommended | Training + report-out tied to piecework pay |

**If any of the first three is missing, the full WIP / MES loop is high-cost and high-risk.** Recommended approach: start with mid-layer capabilities (tooling check-out + asset counts + supply ledger), stabilize for 3–6 months, then evaluate the top layer.

## V. AssetaGuard capabilities you can use today

| Capability | Status | Business value |
| --- | --- | --- |
| Tooling and fixture check-out (handheld + badge) | ✅ Shipped | Tool find time 30 min → 30 sec |
| Item-finder mode (Geiger-style) | ✅ Shipped | Find a specific fixture in a pile in 30 sec |
| Monthly full-asset count (walk the handheld) | ✅ Shipped | 1000 items in 30 sec |
| Asset full lifecycle (status / maintenance / retirement) | ✅ Shipped | Timeline + operator + approval audit |
| Supply ledger (consumable SKU in/out) | ✅ Shipped | Same-day visibility |
| Online / offline dual-mode handheld | ✅ Shipped | Works in low-signal shops |
| ERP integration (Yonyou / Kingdee / custom) | ✅ Shipped | Standard REST API + CSV |
| Overdue alerts (escalates to crew lead) | ✅ Shipped | Doesn't force returns, but eliminates dispute room |

**This layer alone solves 80% of shop-floor pain.**

## VI. Roadmap top-layer capabilities (in co-build)

| Capability | Status | Co-build value |
| --- | --- | --- |
| WIP gate readers + auto-report-out | 🛣️ Roadmap | Co-design hardware solution with first manufacturing pilots |
| Real-time bidirectional MES integration | 🛣️ Roadmap | Project-based per MES type |
| On-metal / high-temp tag field kits | 🛣️ Roadmap | For casting / welding / heat treatment |
| Gauge calibration cycle closed loop | 🛣️ Roadmap | Calibration management + gate-reader rules |
| Equipment inspection SOP + maintenance work orders | 🛣️ Roadmap | SOP form engine + multi-role work orders |
| Maintenance cycle reminders | 🛣️ Roadmap | By time / by use count / by mold strokes |
| IoT integration for predictive maintenance | 🛣️ Roadmap | Equipment runtime + asset record |

## VII. Why we want to build this with you

WIP / MES + RFID is a **highly customized direction** — every factory's process routing, MES system, shop environment, and worker culture are different. **A universal product is hard; a customer + industry template is feasible.**

Our strategy:
- Help customers get visible 3-month ROI with mid-layer capabilities (tooling check-out + asset counts) first
- Co-build WIP / MES with 1–2 representative manufacturing customers
- Distill into a reusable template for later customers

## VIII. Co-build invitation

If your factory matches the following, let's talk:

- Asset / tooling / equipment scale > 1000 items
- Monthly shrinkage / find-time has become an operational pain point
- Willing to start with tooling check-out + asset counts and see results in 3 months
- If you need real-time MES integration, your factory IT team can support API integration

[Contact us / apply for the manufacturing pilot](/en-US/trial)

---

> 📌 **About this article**: ✅ Shipped capabilities are available in the current AssetaGuard product and validated by customers. 🛣️ Roadmap capabilities are co-build directions, not sales commitments. Specific capability boundaries are confirmed in the requirements workshop.
