---
title: Asset & Supply Tracking for Livestream MCN Studios — RFID Solution
description: Two-track inventory for MCN agencies and livestream commerce — RFID-tagged assets (cameras, lights, samples, props) for individual tracking; consumables tracked by SKU. Check-in/out by person, return reconciliation, monthly cycle counts.
date: 2026-05-11
industry: livestream
tags: [MCN, livestream commerce, RFID, asset management, supplies]
author: AssetaGuard team
readingMinutes: 6
heroBullets:
  - Two-track model — RFID for assets, ledger for supplies
  - Handheld scans 200 items in 5 seconds, item-finder mode locates a single piece
  - Personal check-out logs with overdue alerts
callToAction: Apply for the livestream MCN pilot
---

## TL;DR

The hardest part of running an MCN warehouse is **chaotic flow of livestream gear and product samples, talents borrowing without returning, and consumable supplies that never reconcile**. AssetaGuard splits the inventory into two tracks: **assets** (production gear, sample products, props) get RFID tags and per-piece tracking; **supplies** (packaging, gifts, consumables) are tracked as SKU-level ledger entries. Five seconds to count 500 assets, monthly shrinkage drops from 8% to under 0.3%.

## First, separate "assets" from "supplies"

Not everything in a livestream studio needs an RFID tag — that wastes both money and labor. AssetaGuard splits items by whether they need per-piece tracking:

| Type | Examples | Method | RFID? |
| --- | --- | --- | --- |
| **Assets** | Cameras, key lights, monitors, teleprompters, computers, microphones, on-air samples, props, costumes | One item, one tag — log every check-out / check-in / count | ✅ Yes |
| **Supplies** | Packaging boxes, polymailers, gift cards, cotton pads, cleaning consumables | SKU-level in/out ledger, monthly physical count | ❌ No |

Assets answer "who took it, when do they return it, did anything go missing?" Supplies answer "how much came in, how much went out, what's left?" Both live in the same system but use different workflows.

## Five real pain points in MCN livestream operations

| Scenario | Without a system | Consequence |
| --- | --- | --- |
| Supplier sends new gear / samples | Manual paper checks, mixed colors and sizes | Wrong sample on air, broadcast halts |
| Talent / assistant borrows | "I took five" in a WeChat group | Month-end count never matches |
| Returns from livestream | Manual barcode scan + judgment call | Counterfeits enter resale stream |
| Periodic inventory | One person, 800 items per day | 5%–10% monthly variance written off as shrinkage |
| Consumable requisitions | Paper slips or group chat | Ledger and reality diverge |

## Eight things you actually do with the system

### 1. Tag at receiving
Gear or samples arrive → handheld scans the supplier slip → tag ID auto-binds → SKU, batch, and supplier recorded. New staff are productive in 30 minutes.

### 2. Scan-to-identify — one tap and you know what it is
Scan any RFID tag → instantly see the full asset card: name, spec, current owner, location, borrowing history.
- Found an unmarked sample in the warehouse? Scan and the owner appears.
- Reconciling returns? One scan and you see the original shipment record.

### 3. Item-finder mode (Geiger-counter style locator)
Know the asset ID but can't find the physical item? Switch the handheld to **finder mode** — enter the target tag, then real-time signal feedback (stronger = closer) leads you to it.
- Need a specific sample right before going live: 30 seconds to spot it in the pile.
- Suspect a "borrowed" item is still in the warehouse: narrow the search radius.

### 4. Talent check-out — one scan
Talent picks samples or borrows gear → handheld scan → system generates a check-out record (with photo and return deadline) attached to that talent's account. **Overdue items trigger an alert in the system**, routed to the warehouse lead and supervisor (the system does not send automated SMS or in-app reminders to the talent — chase actions stay with the management process).

### 5. Return reconciliation
Returned shipment → handheld over the box for 5 seconds → system compares against the original send-out → missing items, wrong items, or counterfeits (no tag / tag ID not in the original shipment) trigger an immediate alert.

### 6. Monthly full count
Walk the handheld along the shelves, 1000 assets read in 30 seconds → variance report auto-generated → accountability traced to the most recent borrower or out-handler.

### 7. Supply ledger
Consumables flow through in/out documents in the system, accumulated by SKU. Monthly physical reconciliation logs any variance with reasons. No RFID, but shares the same permission model, reports, and approvals.

### 8. Asset full lifecycle (status / maintenance / retirement)
Cameras, key lights, teleprompters, even product samples — every piece has a lifecycle. AssetaGuard threads it together:

- **Status changes**: in-use / idle / repair / retired, four states with timestamped operator records — no more "is this light actually broken or not" debates.
- **Maintenance / repair logs**: send-outs for repair, costume cleaning returns, all logged on the asset detail page.
- **Lifecycle view**: receiving → talent borrowing history → maintenance records → retirement / supplier return, one timeline that makes talent settlement and supplier reconciliation easy.
- **Retirement / disposal**: out-of-season samples or broken gear go through a retirement form → supervisor approval → removed from the active asset pool.

## Before / after

| Metric | Before | With AssetaGuard |
| --- | --- | --- |
| Single asset count (500 items) | 6 hours | 4 minutes |
| Monthly asset shrinkage | 5%–10% | < 0.3% |
| Talent borrowing trace | WeChat messages | System record + photo + signature |
| Return authentication | Judgment call | Tag-based verification |
| Supply ledger gap | Discovered at month-end | Visible same-day |
| Asset record / maintenance log | Excel + paper + WeChat group | System timeline + operator + approval audit |
| Monthly shrinkage cost (1M asset pool est.) | ¥50K–¥100K | < ¥3K |

## 7-day rollout

| Day | Action |
| --- | --- |
| D1 | Baseline asset pool + supply SKU list, AssetaGuard trial account |
| D2 | Tag the first 1000 assets, import supply SKUs |
| D3 | Train warehouse and talent assistants (< 1 hour) |
| D4–6 | Run 3 days of real operations (check-out / return / reconcile / supply requisition) |
| D7 | Data review + decide on full warehouse rollout |

## FAQ

**Q: We already have an ERP — do we need this too?**
ERP manages the books; AssetaGuard manages the physical items, especially per-piece traceability for assets. The two integrate (Yonyou, Kingdee, custom systems). AssetaGuard does not replace your ERP.

**Q: If a talent doesn't return borrowed items, can the system force them?**
The system can't "force" anyone, but **overdue items automatically generate alerts** that escalate to the warehouse lead and supervisor by rule. AssetaGuard makes "who, when, what, still out" crystal clear — the chase action remains a management process, but disputes drop to zero.

**Q: Do small items like packaging and gift cards need RFID tags?**
No. Those are "supplies" — SKU-level in/out tracking is enough. Only items that need per-piece traceability (gear, samples, props) get RFID tags.

**Q: Are the tags expensive?**
Flexible tags ¥0.3–0.8 each, on-metal tags ¥1–3 each. Compared to a sample garment worth ¥200–2000 or a key light worth several hundred to several thousand, tag cost is negligible.

## Next step

Five MCN pilot slots open each month, with the livestream asset template (gear / samples / props) and supply ledger pre-configured. [Apply for the pilot](/en-US/trial).
