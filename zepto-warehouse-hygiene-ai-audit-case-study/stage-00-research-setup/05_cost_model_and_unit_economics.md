# Cross-Stage Cost Model — Verified Hygiene Check

**Prepared:** 2026-08-10
**Status:** Reference implementation economics; not Zepto’s actual invoice or internal budget

## What “actual cost” means here

Zepto’s payroll rates, cloud contracts, store count, existing-device policy, inspection-vendor rates, and internal engineering cost are not public. It would be misleading to invent those values.

This model therefore separates:

1. **Public vendor list prices** used as auditable inputs.
2. **Explicit Zepto finance/operations inputs** that must replace assumptions.
3. **Illustrative planning scenarios** for deciding whether the approach is economically viable.

Prices are a snapshot, not a quote. Re-run the model at procurement time.

## Reference implementation assumptions

| Variable | Reference value | Type |
|---|---:|---|
| Scan duration | 15 minutes | Product assumption |
| AI input | Full video, sampled at 1 FPS, low media resolution for screening | Product assumption |
| Low-resolution video tokens | 100 tokens/second | Google documentation reference |
| Default-resolution video tokens | ~300 tokens/second | Google documentation reference |
| AI output | 1,000 tokens per scan | Product assumption; verify from usage logs |
| Evidence upload | 100 MB per scan | Engineering assumption; measure after compression tests |
| Raw-media retention | 30 days | Privacy/policy assumption |
| Checks per warehouse | 2/week ≈ 8/month | Pilot assumption |
| Currency conversion | ₹96.25/USD | Rounded reference snapshot from RBI public exchange-rate display; not a locked FX rate |
| Manager loaded cost | ₹200/hour | Zepto Finance input placeholder |
| QA review sample | 10% of scans, 5 minutes each | Pilot assumption |
| QA loaded cost | ₹400/hour | Zepto Finance input placeholder |
| Physical audit allocation | ₹5,000 per random audit, 1/quarter | Procurement placeholder, not a public Zepto rate |
| Tag cost | ₹200 per store QR/NFC kit, amortised over 24 months | Procurement placeholder |

## Public price inputs

### AI inference

Google’s current Gemini API pricing lists Gemini 2.5 Flash-Lite at **$0.10 per 1M input tokens** for text/image/video and **$0.40 per 1M output tokens**. Gemini 2.5 Flash is listed at **$0.30 per 1M input tokens** and **$2.50 per 1M output tokens**. [Gemini API pricing](https://ai.google.dev/gemini-api/docs/pricing)

Google’s video documentation states that low-resolution video is approximately **100 tokens/second**, while default-resolution video is approximately **300 tokens/second**. It also recommends checking actual usage through the API response. [Gemini video understanding](https://ai.google.dev/gemini-api/docs/video-understanding), [Gemini token counting](https://ai.google.dev/gemini-api/docs/tokens)

### Storage, notifications, and backend

- Firebase Cloud Messaging is listed as a no-cost product. [Firebase pricing](https://firebase.google.com/pricing)
- Firebase Storage’s listed default-bucket example is **$0.026/GB-month** after the applicable no-cost allowance, with upload/download request charges that are negligible at one object per scan but must still be metered. [Firebase pricing](https://firebase.google.com/pricing)
- Cloud Run request-based billing lists **$0.000024/vCPU-second**, **$0.0000025/GiB-second**, and **$0.40 per 1M requests** at the default Tier 1 rate; Mumbai is included in Google’s Tier 1 region list. [Cloud Run pricing](https://cloud.google.com/run/pricing)
- For conversion only, this model uses a rounded **₹96.25/USD** reference from the RBI public exchange-rate display. Finance should replace it with the actual billing/treasury rate. [RBI exchange-rate archive](https://www.rbi.org.in/scripts/ReferenceRateArchive.aspx)

## Per-scan calculation

### 1. AI cost

**Low-cost screening pass**

```text
Input tokens = 15 min × 60 sec × 100 tokens/sec = 90,000
Input cost   = 90,000 / 1,000,000 × $0.10 = $0.0090
Output cost  = 1,000 / 1,000,000 × $0.40 = $0.0004
AI total     = $0.0094 ≈ ₹0.90 per scan
```

**Default-resolution Gemini 2.5 Flash pass**

```text
Input tokens = 15 min × 60 sec × 300 tokens/sec = 270,000
Input cost   = 270,000 / 1,000,000 × $0.30 = $0.0810
Output cost  = 1,000 / 1,000,000 × $2.50 = $0.0025
AI total     = $0.0835 ≈ ₹8.04 per scan
```

The model must verify actual token usage. A 10% high-resolution or premium-human-review fallback would increase average AI cost; for example, using Gemini 2.5 Pro on 10% of default-resolution scans adds roughly ₹3–₹4 per average scan under the prices above. This is an estimate, not a measured result.

### 2. Digital infrastructure cost

| Component | Calculation | Reference cost / scan |
|---|---|---:|
| AI screening | Low-resolution Flash-Lite scenario above | ₹0.90 |
| Evidence storage | 0.1 GB × $0.026/GB-month × ₹96.25/USD | ₹0.25 for 30-day storage |
| Cloud Run orchestration | 1 vCPU + 0.5 GiB for 60 seconds, two requests, before free tier | ≈₹0.15 |
| Push notification | FCM | ₹0 |
| Mobile data | 0.1 GB × Zepto’s contracted ₹/GB | **Input required**; at ₹20/GB, ₹2.00 |
| QR/NFC tag amortisation | ₹200 ÷ 24 months ÷ 8 monthly scans | ≈₹1.04 |
| **Digital subtotal with ₹20/GB data scenario** | — | **≈₹4.34** |

The digital subtotal is not the total cost of a check. It excludes people, physical audits, support, platform fixed costs, and exception handling.

### 3. Operating cost per scan

| Component | Calculation | Reference cost / scan |
|---|---|---:|
| Manager capture time | 15/60 hour × ₹200/hour | ₹50.00 |
| QA sample review | 10% × 5/60 hour × ₹400/hour | ₹3.33 |
| Critical-exception reserve | 2% × 20/60 hour × ₹400/hour | ₹2.67 |
| Digital subtotal | From table above | ₹4.34 |
| **Run-rate before independent physical audit** | — | **≈₹60.34 per scan** |

### 4. Independent audit allocation

The proposal deliberately retains random physical audits. With the reference assumption of one ₹5,000 audit per quarter and 26 scans per warehouse per quarter:

```text
Physical-audit allocation = ₹5,000 / 26 scans ≈ ₹192.31 per scan
```

Therefore:

```text
Fully loaded operating cost = ₹60.34 + ₹192.31 ≈ ₹252.65 per scan
```

The physical-audit line is a procurement placeholder. It is the most sensitive cost input and must be replaced with Zepto’s actual vendor, travel, sampling, and lab-testing cost.

## Per-warehouse and network view

Using 8 scans per warehouse per month:

| Scope | Digital only | Run-rate before physical audits | Fully loaded with audit allocation |
|---|---:|---:|---:|
| One warehouse / month | ₹35 | ₹483 | ₹2,021 |
| 1,000 warehouses / month | ₹35,000 | ₹4.83 lakh | ₹20.21 lakh |

These figures exclude one-time build cost, taxes, negotiated discounts, model retries, media egress, support management, and unexpected re-checks. They are planning scenarios, not Zepto actuals.

## Full lifecycle cost from research to scale

| Stage | Cost category | How to calculate actual Zepto cost | Illustrative planning range |
|---|---|---|---:|
| 00 Research setup | Public research, PM, food-safety, legal/privacy time | Hours × each team’s fully loaded rate; public research cash can be ₹0 without paid data | ₹1–3 lakh |
| 01 Discovery | Labelled media, reviewer calibration, data preparation | Cases × reviewers × minutes × loaded rate + secure handling | ₹1–5 lakh |
| 02 Define/prioritize | Product, operations, food-safety, legal workshops | Workshop hours × loaded rates | ₹1–4 lakh |
| 03 Solution design | UX, service blueprint, threat model, prototype | Design/engineering/security hours × rates | ₹3–8 lakh |
| 04 Product delivery | Mobile capture, backend, reviewer console, integrations, QA | Engineering hours + vendor setup + security/privacy assessment | ₹30–60 lakh for a planning model; replace with Zepto estimate |
| 05 Shadow pilot | Tags, training, review operations, scans, physical calibration | Per-store setup + scans × unit cost + reviewer/audit time | ₹5–15 lakh plus scan costs |
| 06 Launch/scale | Run-rate per scan, fixed platform, support, audits, model monitoring | `N × scans/month × unit cost + fixed monthly cost` | Must be calculated from actual store count and cadence |
| 07 Handoff | Quarterly calibration, independent audit, post-launch review | Audit/review cadence × vendor and internal rates | Ongoing operating budget |

The ranges above are deliberately labelled planning assumptions. Only vendor list prices in the preceding sections are public prices; internal labour, engineering, audit, and procurement lines need Zepto Finance/Procurement confirmation.

## One-time cost amortisation

For a business case, show both views:

```text
Cash run-rate per scan = variable scan cost + audit allocation

Fully loaded per scan = cash run-rate per scan
                         + one-time program cost / expected lifetime scans
                         + fixed platform cost / expected scans
```

Illustrative example: if one-time program cost is ₹60 lakh, the network has 1,000 warehouses, and each runs 8 scans/month for 12 months, the one-time allocation is:

```text
₹60,00,000 / (1,000 × 8 × 12) = ₹62.50 per scan
```

That would make the reference fully loaded cost approximately **₹315 per scan** before taxes and unplanned re-checks. This is a sensitivity example, not a claim about Zepto’s budget.

## Sensitivity: what actually moves the number

| Driver | Low case | Reference | High case | Cost impact |
|---|---:|---:|---:|---|
| Scan length | 10 min | 15 min | 20 min | AI and upload cost scale roughly with duration; manager time also increases |
| AI resolution/model | Flash-Lite low-res | Flash-Lite + selected escalation | Flash / Pro high-res | AI can move from <₹1 to tens of rupees per scan; still smaller than labour/audits |
| Evidence size | 50 MB | 100 MB | 200 MB | Storage remains small; mobile data and retention grow linearly |
| Manager loaded rate/time | ₹150/h × 10 min | ₹200/h × 15 min | ₹300/h × 20 min | ₹25 to ₹100 per scan |
| QA sampling | 5% × 5 min | 10% × 5 min | 20% × 15 min | ₹1.25 to ₹30 per scan at ₹300–₹600/h |
| Independent audit | ₹3,000/quarter | ₹5,000/quarter | ₹10,000/quarter | About ₹115 to ₹385 per scan at 26 scans/quarter |

## Economic conclusion

The proposal is economically plausible because token inference and basic cloud services are inexpensive at the per-scan level. The real business decision is whether Zepto values the additional control enough to fund manager time, QA adjudication, independent audits, remediation, privacy/security, and one-time integration.

The product should therefore be approved only with a **cost-per-verified-control** metric, not AI cost alone:

```text
Cost per verified-control store-day
= total program cost / store-days with complete evidence and no unresolved critical issue
```

## Cost data required before pilot approval

- Zepto’s loaded hourly rates for manager, QA, Food Safety, Engineering, Legal, and Privacy roles.
- Actual average video size and duration from a compression test.
- Cloud contract/region, retention, egress, backup, and logging costs.
- Model usage logs from a small offline replay.
- Real QA review rate and exception frequency.
- Physical audit/vendor quote, sampling/lab costs, travel, and cadence.
- Store count, check cadence, manager device policy, and tag procurement quote.
- Expected lifetime and amortisation policy for the one-time MVP investment.

## Stage 0 cost gate

**Decision:** Add cost as a first-class feasibility gate before shadow-mode execution.

**Recommendation:** Approve the reference model for planning, then replace all internal placeholders with Zepto Finance/Procurement inputs before committing to scale.

**Strongest finding:** AI inference is estimated at roughly ₹0.90–₹8.04 per scan using current public Gemini list prices and explicit token assumptions; labour and independent physical audits dominate the reference total.

**Open questions:** Actual loaded labour rates, physical-audit quote, media size, cloud contract, and Zepto’s expected store/check volume.
**Approval request:** Approve collecting these cost inputs before the shadow-mode budget is finalised.
