# FarmBridge: Fair-Price Produce Matching and Shared Logistics

**Smart India Hackathon 2026 | Problem Statement 26033**  
**Date:** 22 November 2026  
**Reference Number:** 26015785  
**Applicant:** Sugavarman K P

## Problem Title

Multiple intermediaries reduce farmers' earnings and increase consumer prices.

## Problem Creator's Organization

Ministry of Consumer Affairs, Food & Public Distribution

## Theme

Agriculture, FoodTech & Rural Development

## Problem Description

Farmers and Farmer Producer Organisations (FPOs) can lose bargaining power and price visibility when produce passes through several trading and handling stages. Aggregation, grading, storage, transport, and market access provide real services, so the goal is not to remove every intermediary. The goal is to make avoidable costs visible, connect producer groups to suitable buyers, and coordinate logistics so farmers can compare the net return before accepting a sale.

The SIH problem asks for a digital marketplace that connects farmers/FPOs with consumers and bulk buyers, provides logistics support, and uses AI for demand forecasting and route optimization. The intended benefits are better prices for farmers, lower prices for consumers, and fewer supply-chain inefficiencies.

## Proposed Solution: FarmBridge

FarmBridge is a mobile-first marketplace and shared-logistics coordinator for FPOs, farmer groups, local retailers, restaurants, hostels, institutional kitchens, and nearby consumer groups. It focuses on completing a dependable sale after produce is listed: matching compatible supply and demand, making every estimated charge visible, and planning shared collection and delivery.

A farmer or FPO listing records the crop, quantity, grade, harvest window, collection point, photos or weigh-slip evidence, and minimum acceptable farm-gate price. Buyers post quantity-backed requests with a delivery area and date. FarmBridge filters out infeasible matches, estimates packing, handling, and transport costs, then ranks eligible offers by expected net farmer return, freshness fit, distance, and buyer fulfilment history. The FPO reviews the itemised calculation and accepts, rejects, or waits; the platform never sets the farmer's reserve price or commits a sale automatically.

### Main workflow

1. A farmer creates a listing with local-language text, a voice-assisted form, or help from an FPO operator.
2. The FPO weighs and grades the lot at a collection point and records available evidence.
3. Nearby retailers and institutional or consumer buyers post demand with quantity, grade, delivery area, and date.
4. FarmBridge checks crop, quantity, date, grade, service area, and buyer status, then shows eligible offers with the expected net payout and itemised costs.
5. The FPO confirms an offer. The logistics planner groups accepted orders into a feasible route based on vehicle capacity, pickup windows, delivery windows, and perishability.
6. Both parties receive an order record and status updates. Actual weight, delivery, cost, settlement, and any dispute are recorded against the order.

### How it addresses the problem

- **Better farmer price visibility:** the FPO sees the expected payout after disclosed charges before accepting an offer.
- **Fewer avoidable trading hops:** producer groups can reach local retailers and bulk buyers directly while still paying for genuine logistics and handling services.
- **Economical small-lot sales:** compatible lots can be pooled so small producers can serve buyers that need more volume.
- **Lower delivery cost where pooling works:** route suggestions allocate estimated transport costs across compatible orders and show whether consolidation reduces cost.
- **Reduced uncertainty:** demand history helps FPOs plan listing and collection windows. Unsold lots remain visible for another buyer or the FPO's usual market channel.
- **Farmer control and accountability:** FPOs retain the sale decision; price, weight, charges, delivery, and settlement changes have an audit trail.

### Innovation and uniqueness

FarmBridge ranks offers by expected net farmer return rather than headline price alone. Its open-book cost card separates produce price, grade, quantity, packing, handling, transport, any platform fee, and estimated farmer payout. Small-lot pooling keeps each farmer's contribution and payout traceable. Matching and routing provide recommendations for human review; they do not make binding price or sale decisions.

## Technical Approach

### Architecture and technologies

- **Farmer/FPO and buyer interfaces:** responsive React Progressive Web App with English and Tamil UI, low-bandwidth screens, offline draft listings, and queued synchronization.
- **Operator console:** web tools for FPO-assisted onboarding, weighing, grading, order confirmation, disputes, and route review.
- **API and access control:** Python FastAPI or Django REST Framework with validated requests, role-based permissions, and an auditable order workflow.
- **Data:** PostgreSQL with PostGIS for lots, buyer requests, service areas, and distance queries; object storage for produce photos and delivery evidence.
- **Matching:** deterministic eligibility checks first, followed by a published score using net return, freshness/date fit, distance or delivery cost, and buyer fulfilment history.
- **Demand estimation:** begin with a seasonal moving-average baseline by crop, service area, and week. Evaluate a simple tree-based model only after enough clean, dated order history exists. Show coverage and uncertainty and allow operator review.
- **Route planning:** OR-Tools or an equivalent vehicle-routing solver with capacity, pickup and delivery windows, and perishability constraints. A logistics operator confirms each suggested route before dispatch.
- **Notifications and security:** SMS or an approved messaging adapter for status updates; HTTPS, password hashing or an approved identity provider, least-privilege roles, audit logs, encrypted backups, and data minimisation.

### Data and model safeguards

Forecasts should use pilot records such as dated buyer requests and completed orders by crop, grade, quantity, and service area. Public market-price series can support price context but are not a substitute for local demand labels. If history is insufficient, FarmBridge will show the baseline and its limitations instead of presenting an unreliable model output. Forecasts will never promise a price or automatically commit produce for sale.

### Implementation stages

1. Build listings, buyer requests, assisted FPO workflows, and transparent offer comparisons.
2. Add order status, evidence, settlement records, and operator-confirmed route suggestions.
3. Run a compact pilot and measure price, fulfilment, logistics cost, and data quality.
4. Add model comparisons only when the pilot has enough reliable history; integrate external platforms or payment services only with partner approval and field validation.

## Feasibility and Viability

### Pilot feasibility

Start in one district with two or three FPOs, a small set of perishable crops, fixed collection points, and nearby repeat buyers such as retailers or institutional kitchens. Use existing Android phones, assisted onboarding, a hosted web service, and local transport partners. Keep match and route confirmation manual during the first pilot stage. Use clearly labelled synthetic records for the demonstrator; do not claim guaranteed demand, guaranteed prices, live payments, or production forecasting before validation.

### Risks and mitigations

| Risk | Mitigation |
|---|---|
| Quantity or grade mismatch | FPO-assisted weighing, a simple grade checklist, photo or weigh-slip evidence, and buyer acceptance rules |
| Low adoption or weak connectivity | Tamil-language PWA, assisted onboarding, phone/SMS updates, and offline draft sync |
| Too few orders for pooled routes | Begin in a compact area, show whether pooling lowers cost, and keep existing channels available for unmatched lots |
| Forecast error or seasonal shock | Start with a baseline, display uncertainty, measure error, and never auto-commit a sale from a forecast |
| Cancellations or side-selling | Confirmation reminders, clear reservation windows, fulfilment history, and human-mediated dispute handling |
| Perishability or delivery delay | Short delivery windows, vehicle capacity limits, cold-chain flags where needed, and fallback buyer/channel options |
| Hidden fees or price manipulation | Disclose every charge before acceptance and retain a change log for price, weight, and payout records |
| Privacy or account misuse | Minimise personal data, use role-based access, secure backups, retention rules, and account recovery safeguards |
| Local market-rule differences | Configure the pilot for local requirements and obtain market-partner and legal review before expansion |

### Sustainability

During the pilot, operations can be funded through a grant, an institutional buyer subscription, or an FPO service contract. If a transaction fee is introduced later, disclose it before acceptance and assess its effect on farmer net returns. Keep core listing and offer-comparison functions usable on low-end phones.

## Impact and Benefits

The pilot will compare FarmBridge orders with the same FPO's usual-channel sales for comparable crops and weeks. Results will include sample sizes and will be reported as pilot observations, not proven causal effects.

- **Farmer economics:** net amount received per kilogram, time from listing to sale, and share of lots sold within the intended window.
- **Buyer economics:** delivered price per kilogram, fill rate, and repeat purchase rate.
- **Operations:** transport cost per kilogram, vehicle utilisation, delivery timeliness, and spoilage or quality-rejection rate.
- **Inclusion:** active smallholder share, assisted versus self-service listings, Tamil-language use, and successful low-connectivity syncs.
- **Trust:** disputes per 100 orders, payout completion time, and orders with complete price and weight records.

Expected benefits to validate are clearer price discovery and bargaining for farmers, more predictable local sourcing for buyers, lower per-order transport costs when trips are successfully pooled, and less avoidable handling. Environmental benefits will be claimed only if measured route distance and load data show a reduction.

## Prototype Scope and Demonstration

The first demonstrator includes FPO login, create/edit lot, buyer demand request, transparent offer comparison, accept/reject action, basic multi-stop route suggestion, order status, and a dashboard of farmer net return and delivery cost.

Demo flow: create two synthetic lots and one nearby buyer request; show eligibility checks and itemised net-return comparison; accept an offer as the FPO; display the pooled route, vehicle capacity, estimated distance, and cost allocation; record delivery and settlement; then show the dashboard and demand baseline with its data coverage. All sample records are synthetic and will be labelled as such.

Government-platform integration, live payment processing, and production-grade forecasting are future work requiring partner access, compliance review, and field validation.

## Research and References

1. SIH 26033 workshop template and problem statement: https://github.com/selvasachein/SIH-26033
2. e-NAM, information for FPOs: https://www.enam.gov.in/web/stakeholders-Involved/fpos
3. e-NAM, trading and logistics features: https://www.enam.gov.in/web/trading-details
4. Department of Consumer Affairs, Price Monitoring Division: https://consumeraffairs.gov.in/pages/price-monitoring-division
5. Small Farmers' Agri-Business Consortium (SFAC), State Level Consortium of FPOs: https://sfacindia.com/State-Level-Producer-Companies.aspx
