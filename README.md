# Deployable power electronics

**Electronics Engineer · [Cognitive Advantage](https://www.linkedin.com/company/cognitive-advantage-pty-ltd/)**

> **Public case study only** — no proprietary source, schematics, or customer-confidential detail.  
> Summary of work by Tanmeet Singh Sachdeva for portfolio purposes.

---

## Problem statement

Field-deployable hardware needed reliable **12 V / 24 V power conversion**, **automatic source selection**, and **ride-through** when mains or generator inputs dropped — without an operator babysitting the rack.

## High-level impact

- **~97%** measured efficiency on buck-boost conversion paths used in deployment.
- **Sub-2 ms** automatic switch between power sources under load.
- Capacitor-based **UPS** layer to maintain continuity during brief input loss.
- Reduced manual power intervention during deployable operations.

## My contribution

- Designed and built **control / power-selection boards**, **buck-boost supplies**, and the **capacitor UPS** integration.
- Owned bring-up and validation: load steps, source failover timing, and interaction with downstream equipment.
- Worked across **power conversion, switching logic, embedded control**, and the systems being powered so the stack behaved as one product.

## Tech and design choices

| Choice | Why |
| --- | --- |
| **Buck-boost** for 12 V / 24 V rails | Single topology covered wide input variation vs separate fixed buck-only rails per voltage. |
| **Dedicated selection + control board** | Kept high-current paths and logic isolated; easier to test failover without re-spinning power stages. |
| **Capacitor UPS** (vs battery UPS) | Short hold-up for transients and switchover; lighter and simpler for the required ride-through window. |
| **Embedded supervision of switch timing** | Software-defined sequencing allowed tuning **&lt;2 ms** failover after bench measurement, vs purely analog interlocking only. |

## Lesson / twist

**Load-step transients** during automatic source change caused downstream resets until switch sequencing and inrush limiting were aligned with the UPS hold-up time — fixed by reordering enable lines and validating with scoped failover tests under realistic load, not no-load bench checks alone.

---

**Context:** [Portfolio](https://tanmeetsingh24.github.io) · Cognitive Advantage · deployable defence-adjacent systems.
