# Website Idea Validation Framework
## From Pitch to Product: A Step-by-Step Guide

# Introduction

You have 4 pitch ideas. The competitive analysis revealed:
- **Pitch 1 (EV Charging)**: Partial competition - needs differentiation
- **Pitch 2 (Circular Materials)**: High competition - risky
- **Pitch 3 (Urban Heat)**: Strong - simulation feature is unique
- **Pitch 4 (Danish Heat-Link)**: Strongest - no competition, documented need

**Now what?** This framework will help you validate which idea to actually build.

---

# Phase 1: Market Validation (Week 1-2)

## Step 1: Identify Your Decision Criteria

Before investing time/money, define what "worth developing" means to you:

### Financial Criteria:
- [ ] Minimum annual revenue target: €______
- [ ] Maximum investment you can afford: €______
- [ ] Time to first revenue: ______ months
- [ ] Break-even timeline: ______ months/years

### Strategic Criteria:
- [ ] Government contract potential (high/medium/low)
- [ ] Scalability beyond Netherlands (yes/no)
- [ ] Technical complexity you can handle (high/medium/low)
- [ ] Personal interest/passion (rate 1-10 for each idea)

### Impact Criteria:
- [ ] Environmental impact priority (rate importance 1-10)
- [ ] Social impact (communities helped)
- [ ] Political appeal (helps government meet targets)

**Action**: Fill out these criteria for yourself. Be honest about constraints.

---

## Step 2: Quick Market Validation Tests

For each idea, conduct these **low-cost validation tests**:

### A. Problem Validation (Is the problem real?)

**For ALL 4 IDEAS:**

1. **Google Trends Research** (30 min per idea)
   - Search terms related to your problem
   - Is search volume increasing?
   - Are people actively looking for solutions?

   Example queries:
   - Pitch 1: "laadpaal aanvragen" "where to request charging station"
   - Pitch 2: "gemeentelijk restmateriaal" "municipality surplus"
   - Pitch 3: "hittestress steden" "urban heat stress"
   - Pitch 4: "aardgasvrij bezwaren" "gas-free objections"

2. **News Article Scan** (1 hour per idea)
   - Find 5-10 recent articles (2024-2025) about the problem
   - Are municipalities/government actively discussing it?
   - Is there urgency?
   - Are budgets allocated?

3. **LinkedIn Poll** (Optional - 1 week)
   - Post a simple question to gauge interest
   - "What's the biggest blocker to [X]?"
   - Target: municipal officials, urban planners, sustainability professionals

**Decision Point**: If you can't find evidence the problem is actively discussed and has budget behind it, STOP. Don't build it.

---

### B. Solution Validation (Do they want THIS solution?)

**For your TOP 2 IDEAS** (based on Step 2A results):

1. **Landing Page Test** (1 week, ~€100)
   - Create simple landing page describing the solution
   - Use Carrd, Webflow, or simple HTML
   - Include email signup for "early access"
   - Run small Google Ads campaign (€50-100)
   - Target: municipal officials, planners

   **Success metric**:
   - If >5% of visitors sign up → Strong interest
   - If 2-5% → Moderate interest
   - If <2% → Weak interest

2. **Coffee Chat Interviews** (2 weeks, free)
   - Reach out to 10 people who would use your product:
     - Municipal officials (via LinkedIn)
     - Urban planners
     - Sustainability coordinators
     - Energy consultants

   **Script**:
   "Hi [Name], I'm researching challenges around [problem]. Would you have 20 min for a coffee chat? I'm not selling anything, just learning."

   **Questions to ask**:
   - "How do you currently handle [problem]?"
   - "What's the biggest frustration with current approach?"
   - "If I built [solution], would you use it? Why or why not?"
   - "What would you pay for a solution?"
   - "Who else should I talk to?"

   **Success metric**:
   - If 5+ say "I'd definitely use this" → Strong validation
   - If 3-4 → Moderate validation
   - If <3 → Pivot or abandon

3. **Competition Check (Deep Dive)**
   - For your top 2 ideas, spend 2 hours researching:
   - Email 2-3 competitors (if they exist) as a "potential customer"
   - What are their prices?
   - What features do they offer/not offer?
   - What do reviews say? (search "[competitor] review")
   - Can you find their customer list?

   **Decision Point**: Can you clearly articulate why yours is 10x better in ONE sentence? If not, dig deeper or pivot.

---

## Step 3: Government Contract Research

**Critical for your ideas** - all target government. Validate the business model:

### A. Budget Research (1-2 days)

1. **Find Allocated Budgets**:
   - Search: "Rijksbegroting 2025 [your topic]"
   - Check: rijksoverheid.nl/onderwerpen
   - Look for: Klimaatfonds, Gemeentefonds

   For each idea:
   - Pitch 1: Search "laadinfrastructuur subsidie 2025"
   - Pitch 2: Search "circulaire economie subsidie"
   - Pitch 3: Search "hitte adaptatie subsidie"
   - Pitch 4: Search "aardgasvrij budget gemeenten"

2. **Find Recent Contracts**:
   - Check: TenderNed.nl (Dutch government tenders)
   - Search for similar projects awarded in past 2 years
   - Note: Who won? How much? What did they deliver?

**Success metric**: If you find €1M+ in budgets allocated to your problem area → Viable market

### B. Decision Maker Mapping (2-3 days)

Create a list of potential first customers:

**Template**:
```
Municipality: _____________
Contact Person: _____________  (search LinkedIn)
Title: _____________
Email: _____________ (use Hunter.io)
Current Projects: _____________ (check gemeente website)
Budget: _____________ (check begroting)
Pain Point: _____________ (from news articles)
```

**Target**: Map 10 potential customers per idea

**Action**: Send 5 cold emails to gauge interest:

**Email Template**:
```
Subject: Quick question about [problem]

Hi [Name],

I noticed [Municipality] is working on [related project/goal].

I'm developing a tool to help gemeentes with [problem] - specifically [unique benefit].

Would you have 15 minutes for a call to discuss [problem]? I'd love to learn how you're currently handling this.

No sales pitch - just gathering insights.

Best,
[Your name]
```

**Success metric**: If 2+ respond positively → Real interest exists

---

# Phase 2: Technical Feasibility (Week 3)

## Step 4: Can You Actually Build This?

For your TOP 1-2 IDEAS after Phase 1:

### A. Technical Skill Inventory

**Be brutally honest**:

For each idea, rate your ability (1-5):
- Frontend development (React, maps, UI): __/5
- Backend development (databases, APIs): __/5
- Data integration (APIs, scraping, processing): __/5
- Geo-spatial data (maps, PostGIS): __/5
- AI/ML (if needed for predictions): __/5

**Decision rules**:
- If total score <15/25: Can you learn? Do you need a co-founder?
- If <10/25: You need technical help (hire developer or find technical co-founder)

### B. Data Availability Check

Your ideas are data-dependent. Validate data sources:

**Pitch 1 (EV Charging)**:
- [ ] BAG register accessible? (Yes - it's open data)
- [ ] RDW vehicle data? (Check: opendata.rdw.nl)
- [ ] Grid capacity data? (Contact: Netbeheer Nederland)

**Pitch 2 (Circular Materials)**:
- [ ] Do municipalities track surplus? (Ask in interviews)
- [ ] CO2 calculation data? (Check: CO2 emissiefactoren.nl)

**Pitch 3 (Urban Heat)**:
- [ ] ESA Copernicus API access? (Check: scihub.copernicus.eu)
- [ ] KNMI data? (Check: knmi.nl/datacentrum)

**Pitch 4 (Danish Heat-Link)**:
- [ ] Gas consumption data per neighborhood? (CBS open data)
- [ ] Danish benchmarks? (Contact: Danish Energy Agency)

**For EACH data source**:
1. Try to access it (spend 30 min per source)
2. Can you get sample data?
3. Is there API documentation?
4. Are there usage limits/costs?

**Decision Point**: If critical data is inaccessible or prohibitively expensive, that idea is not viable.

---

### C. MVP Scope Definition

For your top idea, define the **Minimum Viable Product**:

**What's the SMALLEST version that proves value?**

**Good MVP Example** (Pitch 4 - Danish Heat-Link):
- Single neighborhood map
- Manual address entry (no auto-complete)
- Simple counter showing %
- Email notification at 70%
- Static cost comparison info
- **Can be built in 4-6 weeks**

**Bad MVP Example**:
- All Netherlands coverage
- AI predictions
- Mobile apps
- Complex simulations
- **Would take 6+ months**

**Action**: Write down MVP scope:
```
Core features (must have):
1. ________________
2. ________________
3. ________________

Nice to have (later):
1. ________________
2. ________________

Definitely NOT in MVP:
1. ________________
2. ________________
```

---

## Step 5: Build vs. Buy vs. Partner Analysis

Before building from scratch, check alternatives:

### Option A: White-label existing solution?
- For Pitch 2: Could you partner with DuSpot/EME as reseller?
- For Pitch 3: Could you add simulation layer on top of Atlas Leefomgeving?

### Option B: No-code/low-code tools?
- Can you prototype with: Bubble.io, Webflow, Airtable, Zapier?
- **Advantage**: Validate faster, cheaper
- **Disadvantage**: Less customizable

### Option C: Build from scratch?
- Only if: You have skills OR budget to hire
- **Advantage**: Full control
- **Disadvantage**: Time, cost, technical risk

**Decision**: For your MVP, choose the FASTEST path to validation.

---

# Phase 3: Financial Viability (Week 4)

## Step 6: Simple Business Model Calculation

For your top idea, do basic math:

### A. Development Costs

**MVP Development**:
- Your time: _____ hours × €___/hour = €_____
- Developer hire (if needed): €_____
- Tools/services (hosting, APIs): €_____
- **Total MVP cost**: €_____

**Full Version** (after validation):
- Add 3-5x the MVP cost: €_____

### B. Customer Acquisition Cost (CAC)

**To get first 10 customers**:
- Marketing/ads: €_____
- Sales time: _____ hours × €___/hour = €_____
- Travel to meetings: €_____
- **Total**: €_____ ÷ 10 = €_____ per customer

### C. Revenue Model

**Pricing Research** (from Step 3):
- Similar tools charge: €_____ per customer
- Government contracts typically: €_____ for comparable projects
- You could realistically charge: €_____ per customer

**Conservative Estimate** (Year 1):
- Number of customers: _____
- Revenue per customer: €_____
- **Total Year 1 revenue**: €_____

### D. Break-Even Analysis

**Simple calculation**:
```
Break-even = Total costs ÷ Revenue per customer
= €_____ ÷ €_____
= _____ customers needed
```

**Can you realistically get that many customers in Year 1?**

**Decision Point**:
- If break-even is >50 customers: Very risky
- If break-even is 10-30 customers: Moderate risk
- If break-even is <10 customers: Low risk

---

## Step 7: Opportunity Cost Assessment

**Be honest about alternatives**:

**Time Investment**:
- MVP will take: _____ weeks
- Full product: _____ months
- Total investment: _____ months of your life

**Alternative uses of that time**:
- Could you earn more doing [other work]?
- Could you pursue a different idea with better validation?
- What's the opportunity cost?

**Passion Test**:
- On a scale of 1-10, how excited are you about this idea? _____
- If <8, why are you doing it?

---

# Phase 4: Decision Matrix (Week 4)

## Step 8: Score Your Ideas

Based on all validation, score each idea:

| Criteria | Weight | Pitch 1 | Pitch 2 | Pitch 3 | Pitch 4 |
|----------|--------|---------|---------|---------|---------|
| Problem is real & urgent | 3x | __/10 | __/10 | __/10 | __/10 |
| Solution validation (interviews) | 3x | __/10 | __/10 | __/10 | __/10 |
| Low competition | 2x | __/10 | __/10 | __/10 | __/10 |
| Budget exists | 2x | __/10 | __/10 | __/10 | __/10 |
| Technical feasibility | 2x | __/10 | __/10 | __/10 | __/10 |
| Data availability | 2x | __/10 | __/10 | __/10 | __/10 |
| Fast MVP possible | 1x | __/10 | __/10 | __/10 | __/10 |
| Break-even <20 customers | 1x | __/10 | __/10 | __/10 | __/10 |
| Your passion for it | 1x | __/10 | __/10 | __/10 | __/10 |
| **TOTAL (max 170)** | | **___** | **___** | **___** | **___** |

**Scoring guide**:
- 10 = Excellent, validated, low risk
- 7-9 = Good, some evidence
- 4-6 = Uncertain, needs more validation
- 1-3 = Weak, red flags
- 0 = Deal-breaker, don't proceed

**Decision rules**:
- Score >120: **GO** - Strong validation, build MVP
- Score 80-120: **VALIDATE MORE** - Do deeper research in weak areas
- Score <80: **PIVOT or ABANDON** - Not worth pursuing

---

# Phase 5: MVP Development (Week 5-10)

## Step 9: Build Minimal MVP

**If your top idea scored >120**:

### Week 5-6: Setup
- [ ] Choose tech stack (based on your skills)
- [ ] Set up development environment
- [ ] Create GitHub repo
- [ ] Design simple wireframes (use Figma or paper)
- [ ] Set up database

### Week 7-9: Core Features
- [ ] Build core feature #1
- [ ] Build core feature #2
- [ ] Build core feature #3
- [ ] Basic styling (doesn't need to be perfect)
- [ ] Manual testing

### Week 10: Polish & Deploy
- [ ] Fix critical bugs
- [ ] Deploy to production (use Vercel, Netlify, or Railway)
- [ ] Create simple landing page
- [ ] Set up analytics (Google Analytics or Plausible)

**Quality bar for MVP**:
- Does it solve the core problem? ✓
- Can someone use it without your help? ✓
- Is it bug-free enough? ✓
- Is it beautiful? ✗ (NOT IMPORTANT FOR MVP)

---

## Step 10: Customer Testing (Week 11-12)

### Get First 5 Users

**Reach out to people from your interviews**:

Email template:
```
Subject: [Product Name] is ready - would love your feedback

Hi [Name],

Remember when we talked about [problem] a few weeks ago?

I built a prototype based on our conversation: [URL]

Would you be willing to test it and give me honest feedback?
Takes about 15 minutes.

I'm especially curious about:
- Does this solve your problem?
- What's confusing?
- What's missing?
- Would you pay for this?

Thanks,
[Your name]

P.S. It's rough around the edges - focus on functionality, not design.
```

### Collect Feedback

**Structure feedback calls** (30 min each):
1. Watch them use it (screen share) - DON'T help
2. Ask: "What are you thinking right now?"
3. Note where they get stuck
4. Ask: "Would you use this weekly? Why or why not?"
5. Ask: "What would make this a must-have?"

**Success metrics**:
- Do 4/5 complete the core task? (Good)
- Do 4/5 say "I'd use this"? (Very good)
- Do any say "I'd pay for this"? (Excellent)

---

## Step 11: Pivot or Proceed Decision

After 5 user tests:

### Proceed if:
✓ Users complete core tasks without help
✓ 3+ say they'd use it regularly
✓ 2+ ask about pricing
✓ Feedback is mostly positive with clear improvement suggestions

### Pivot if:
⚠ Users struggle with core functionality
⚠ 0-1 would use it regularly
⚠ Feedback is "nice idea but..."
⚠ They keep asking for features you can't/won't build

### Abandon if:
✗ You realize the problem isn't painful enough
✗ Building full version would take >1 year
✗ You've lost interest/passion
✗ A competitor launches similar product

---

# Phase 6: Go-to-Market (Week 13+)

## Step 12: First Paying Customer

**Goal: Get someone to pay BEFORE building full version**

### Presale Strategy

**Create a pitch deck** (you already have 4!):
- Use one of your Vivliostyle decks
- Add: MVP screenshots
- Add: User testimonials from tests
- Add: Pricing (start high, discount for early adopters)

**Pricing strategy**:
- Research: What do similar tools charge?
- Anchor high: "Full price will be €10k/year"
- Discount: "Founding customers: €5k/year"
- Include: Setup, training, support
- Limit: "Only 10 founding customer slots"

**Reach out to interested parties from Step 3**:

Email template:
```
Subject: [Product Name] - Founding customer offer

Hi [Name],

Quick update: I built the [product] we discussed.

I'm looking for 10 founding customers to use it for the next 6 months
and help shape the roadmap.

Founding customer benefits:
- 50% off standard pricing (€5k vs €10k/year)
- Lock in this price forever
- Direct input on feature development
- Dedicated support

Interested? Let's schedule a demo.

Best,
[Your name]
```

**Goal**: Get 1 paying customer before investing more time.

---

## Step 13: Iterate or Scale

### If you get 1+ paying customers:

**Iterate** (Months 3-6):
- Deliver what they paid for
- Fix bugs based on real use
- Add most-requested features
- Document everything
- Create case study

**Scale** (Months 6-12):
- Reach out to next 20 prospects
- Improve onboarding
- Create self-service features
- Consider raising prices
- Hire if revenue supports it

### If you DON'T get paying customers after 20 outreaches:

**Hard truth time**:
- Is pricing too high? (Try cutting in half)
- Is MVP too rough? (Polish core features)
- Is timing wrong? (Wait for budget cycle)
- Is problem not painful? (Pivot or abandon)

**Decision**: If after 3 months and 50 outreaches you have 0 customers, STOP.

---

# Summary: Your Action Plan

## Immediate Next Steps (This Week)

**Day 1-2: Decision Criteria**
- [ ] Fill out your personal criteria (financial, strategic, impact)
- [ ] Rank your 4 ideas based on gut feeling

**Day 3-5: Quick Validation**
- [ ] Google Trends research (all 4 ideas)
- [ ] News article scan (all 4 ideas)
- [ ] Identify top 2 ideas based on problem urgency

**Day 6-7: Deep Dive**
- [ ] Coffee chat outreach (send 10 emails per idea)
- [ ] Budget research (find allocated funds)
- [ ] Competition deep dive (your top 2 ideas)

## Week 2-3: Validation

- [ ] Conduct 5 coffee chat interviews
- [ ] Technical feasibility check
- [ ] Data availability verification
- [ ] Complete decision matrix (Step 8)

## Week 4: Build or Abandon

**If score >120**:
- [ ] Define MVP scope
- [ ] Start development

**If score <80**:
- [ ] Pick next best idea and repeat validation
- [ ] OR pivot to different opportunity

## Week 5-10: MVP Development

- [ ] Build core features
- [ ] Deploy to production
- [ ] Get first 5 users testing

## Week 11-12: Validate or Pivot

- [ ] Analyze user feedback
- [ ] Decide: proceed, pivot, or abandon

## Week 13+: First Customer

- [ ] Create sales materials
- [ ] Reach out to prospects
- [ ] Get first paying customer
- [ ] Iterate based on feedback

---

# Key Principles

## 1. Talk to Users EARLY and OFTEN
- Every assumption is wrong until validated
- 10 conversations > 100 hours of coding

## 2. Build Less, Validate More
- Your MVP is probably still too complex
- Cut features until it hurts, then cut more

## 3. Money is Validation
- Interest ≠ Intent
- Intent ≠ Payment
- Only payment validates the business

## 4. Speed Matters
- Spend weeks validating, not months building
- If you can't get 1 customer in 3 months, pivot

## 5. Be Willing to Kill Your Darlings
- Your favorite idea might not be viable
- That's OK - better to learn fast than fail slow

---

# Decision Framework Summary

```
START
  ↓
Quick Validation (Week 1-2)
  ↓
Problem is real + Budget exists?
  ↓ Yes                    ↓ No
Coffee Chats (Week 2)      ABANDON
  ↓
5+ interested?
  ↓ Yes                    ↓ No
Technical Check            PIVOT
  ↓
Can build + Data available?
  ↓ Yes                    ↓ No
Score >120?                PIVOT
  ↓ Yes                    ↓ No
Build MVP (6 weeks)        MORE VALIDATION
  ↓
User testing
  ↓
4/5 would use it?
  ↓ Yes                    ↓ No
Get paying customer        PIVOT
  ↓
First payment received?
  ↓ Yes                    ↓ No
SCALE                      ABANDON
```

---

# Final Recommendation Based on Your Competitive Analysis

## Top Priority: Pitch 4 (Danish Heat-Link)

**Why**:
✓ No direct competition (highest validation score potential)
✓ Documented citizen participation gap (problem is real)
✓ €12B budget allocated (money exists)
✓ 2026 deadline creates urgency
✓ Simulation not required (faster MVP)
✓ Clear customer (342 gemeentes)

**Suggested validation path**:
1. Week 1: Interview 5 municipal heating coordinators
2. Week 2: Interview 3 Danish experts (validate transparency model)
3. Week 3: Build landing page + run €100 Google Ads
4. Week 4: If >10 signups, build MVP
5. Week 5-8: Build MVP (map + counter + email)
6. Week 9: Test with 2 pilot neighborhoods
7. Week 10: Approach first gemeente for pilot contract

**MVP scope**:
- Single neighborhood test
- Manual address entry
- Simple percentage counter
- Email notification at 70%
- One-page cost comparison
- **Can be built in 4 weeks**

## Secondary Option: Pitch 3 (Urban Heat)

**Only pursue if Pitch 4 validation fails**

**Why it's riskier**:
- More technical (simulation algorithms)
- Longer MVP timeline (needs scientific validation)
- More expensive (satellite data processing)

**But has potential because**:
✓ No simulation tool exists
✓ Heat deaths create urgency
✓ Can partner with RIVM/KNMI for credibility

---

# Your Next Action (Right Now)

**Step 1**: Look at your calendar and block time:
- [ ] Week 1-2: 10 hours for validation research
- [ ] Week 3-4: 15 hours for interviews and decision

**Step 2**: Send your first outreach email TODAY:

Find 1 municipal heating coordinator on LinkedIn → Send message:

```
Hi [Name],

I'm researching challenges gemeentes face with the
aardgasvrij transition.

Would you have 20 min for a call? Not selling anything,
just learning about the social acceptance challenges.

Thanks,
[Your name]
```

**Step 3**: Set decision deadline:
- By [Date]: I will decide which idea to pursue
- By [Date]: I will have built MVP or abandoned idea

**The clock is ticking. Talk to users this week.**

