---
title: Prerequisites for Rolling Out RFID Asset Management on the Shop Floor
description: Manufacturing RFID prerequisites — clean asset baseline, tidy supply SKU master data, available ERP interface, worker cooperation mechanism. Gate readers, real-time MES integration, and inspection SOPs are roadmap capabilities and need separate evaluation.
date: 2026-05-10
industry: manufacturing
tags: [manufacturing, RFID, rollout preparation]
author: AssetaGuard team
question: What do you need to prepare before rolling out RFID asset management on the shop floor?
answer: Four core prerequisites — (1) asset baseline must be reconciled first, otherwise the system starts with bad data; (2) supply SKU master data must be tidy, with assets vs. supplies clearly separated; (3) ERP must have a usable interface or CSV import/export; (4) worker cooperation mechanism (training + check-out workflow tied to performance). Factories that prepare well see results in 2 weeks (tooling check-out + monthly counts). Deep scenarios like gate-reader auto-report-out, real-time MES integration, and equipment inspection SOPs are roadmap capabilities and need customer co-build.
---

## Four core prerequisites (must-have)

### Prerequisite 1 — Asset baseline must be reconciled first

The most common failure mode: the system goes live and you discover the actual tooling count is 30% short of the books. **RFID isn't here to "find" tools you already lost — it's here to make sure you don't lose them again.** Spend 1–2 weeks on a thorough manual count to align the baseline before going live.

### Prerequisite 2 — Separate "assets" and "supplies" cleanly

Not everything needs an RFID tag:

| Type | Examples | Method | RFID? |
| --- | --- | --- | --- |
| **Assets** | Tooling, fixtures, molds, gauges, power tools, portable / large equipment | Per-item check-out / check-in / count | ✅ Yes |
| **Supplies** | Bolts, washers, sandpaper, cutting fluid, wipers | SKU-level in/out ledger | ❌ No |

Sort the asset list and the supply SKU list first, then size tag count and system configuration.

### Prerequisite 3 — ERP interface available

AssetaGuard reconciles books and physical inventory with ERPs via **standard REST API + CSV import/export** — it does not replace your ERP:

| ERP system | Integration time |
| --- | --- |
| Yonyou / Kingdee (standard interface) | 1–2 weeks |
| Custom ERP | Depends on the interface, 2–4 weeks |
| No ERP at all | AssetaGuard ships a lightweight asset + supply ledger you can use directly |

⚠️ **Real-time MES integration is not in the current product scope** — please contact us for custom work if needed.

### Prerequisite 4 — Worker cooperation mechanism

Technology isn't the bottleneck. **If people don't cooperate, the system stalls.** Recommendations:
- Training: 30 minutes per worker, the operations are simple (one tap with the handheld)
- Tie the workflow: check-out / check-in tied to the badge / crew performance — cooperation follows naturally
- Don't let workers "back-fill" data manually — that immediately produces fabricated records

## Recommended (not strictly required, but smooths rollout)

### Recommended 1 — Pick a pilot line / pilot shop

Don't roll out plant-wide at once. Pilot one line or one tool crib for 2 weeks first, then evaluate plant-wide rollout pace.

### Recommended 2 — Assess weak-signal stations

Shop floors often have weak or no signal (basement shops, metal-shielded stations, remote facilities). AssetaGuard's mobile app supports **online / offline dual mode** natively — offline cache + auto-sync when network restores — so "no signal" isn't a blocker, but it helps to know which stations are offline ahead of time so you can plan sync timing.

## What you do NOT need to prepare

- **No need to replace your ERP**: AssetaGuard integrates, doesn't replace
- **No need for a working MES**: If you want WIP tracking / MES integration, that's a roadmap direction (see [Factory WIP & MES Integration with RFID — From Shipped Tooling Management Toward WIP Tracking](/en-US/blog/2026-05-manufacturing-wip-rfid)), but **tooling check-out + asset counts + supply ledger** capabilities don't depend on MES
- **No need to roll out plant-wide**: Pilot one line, see data in 2 weeks
- **No need for a 5+ person IT team**: One person to coordinate + one of our deployment engineers is enough

## Additional prerequisites for roadmap capabilities

If your goal goes beyond "tooling check-out + monthly counts" into gate-reader auto-report-out / real-time MES integration / equipment inspection SOPs / calibration reminders, evaluate these additions:

| Roadmap capability | Additional prerequisite |
| --- | --- |
| WIP gate readers | Process routing stable for 3+ months + gate placement design |
| Real-time MES integration | MES system has APIs + IT teams on both sides committed |
| Equipment inspection SOP | SOP form engine requirements workshop |
| Calibration / maintenance reminders | Calibration / maintenance cycle master data tidy |
| On-metal / high-temp tags | On-site environment test + tag selection |

These scenarios are **co-build directions** — AssetaGuard designs and rolls them out with the first manufacturing pilot customers.

## Pace once you're prepared

| Week | Key milestone |
| --- | --- |
| W1 | Asset baseline + supply SKU + tag selection |
| W2 | First batch of tags + worker training + pilot line live |
| W3 | Data comparison + decide on plant-wide rollout pace |

By the end of week 2, tool find time and monthly shrinkage usually show clear improvement.

## Next step

If you meet at least 3 of the 4 core prerequisites, we recommend a tooling check-out + asset count pilot directly. The AssetaGuard manufacturing template includes tooling check-out, asset counts, and supply ledger modules. [Apply for the manufacturing pilot](/en-US/trial).
