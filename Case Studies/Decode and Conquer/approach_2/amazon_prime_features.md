# Case Study: Amazon Prime Feature Development

## Overview
**Question Type:** Service/Platform Design  
**Company:** Amazon  
**Difficulty:** Hard  
**Framework:** Service Design with Data-Driven Approach

---

## Interview Approach

### Step 1: Goals & Constraints (2-3 minutes)

**Clarifying Questions:**
- "What's our primary goal - new member acquisition, retention, or revenue per member?" → *Focus on new member acquisition*
- "Are we constrained to US market or thinking globally?" → *US market for now*
- "Any budget constraints for new features?" → *Should be ROI positive within 18 months*
- "Can we modify the core $139/year pricing?" → *Prefer to keep current pricing*
- "Are we limited to digital features or can we explore physical benefits?" → *Open to both*

**Key Context:**
- Current Prime penetration: ~65% of US households
- Growth slowing as we approach saturation
- Need to attract the remaining 35% who haven't found value compelling

**Success Metrics:**
- Primary: New Prime members (+10M in Year 1)
- Secondary: Conversion rate from free trial (>75%)
- Tertiary: Year 1 retention of new cohort (>85%)

---

### Step 2: Customer Problem Analysis (5-7 minutes)

**Why Haven't Non-Prime Members Joined?**

**Data Analysis Approach:**
"I'd want to look at several data sources:
- Survey data from non-Prime members on barriers
- Behavioral data comparing Prime vs non-Prime shopping patterns
- Demographic analysis of non-Prime segments
- Price sensitivity analysis
- Competitive service adoption (Walmart+, etc.)"

**Non-Prime Segments:**

1. **Price-Sensitive Patty (40% of non-Prime)**
   - Demographics: Household income <$50K
   - Behaviors: Shops deal sites, uses coupons extensively
   - Barrier: $139 feels like too much upfront
   - Current solution: Free shipping thresholds, store pickup

2. **Infrequent Isaac (30% of non-Prime)**
   - Demographics: Rural/suburban, older demographics
   - Behaviors: Shops Amazon 2-3x per year
   - Barrier: Doesn't order enough to justify
   - Current solution: Orders when needed, pays shipping

3. **Alternative Annie (20% of non-Prime)**
   - Demographics: Urban, values local/sustainable
   - Behaviors: Prefers local stores, concerned about Amazon's impact
   - Barrier: Philosophical objections
   - Current solution: Local stores, other online retailers

4. **Cautious Carlos (10% of non-Prime)**
   - Demographics: Mixed
   - Behaviors: Interested but unsure
   - Barrier: Unclear on full value proposition
   - Current solution: Considering but hasn't pulled trigger

**Decision:** Focus on **Price-Sensitive Patty** - largest segment with addressable barriers.

---

### Step 3: Solutions (7-10 minutes)

#### Solution 1: Simple - Prime Lite
**What:** Lower-tier membership at $59/year
**Key Features:**
- Free shipping (5-7 days instead of 2 days)
- Limited Prime Video (with ads)
- Prime Day access
- No Whole Foods discounts

**Pros:**
- Addresses price barrier directly
- Easy to implement
- Clear upgrade path

**Cons:**
- Cannibalizes full Prime revenue
- Might cheapen brand perception
- Margins very thin

#### Solution 2: Medium - Prime Family Savings Hub
**What:** Transform Prime into comprehensive family savings platform
**Key Features:**
- **Grocery Price Match Guarantee**: Beat local store prices by 5%
- **Kids Eat Free Network**: Partner with 10,000+ restaurants
- **Family Rx Savings**: 50% off generic prescriptions
- **School Supplies Subscription**: Auto-deliver at 40% off retail
- **Utility Bill Optimizer**: AI service that reduces bills 10-20%

**Financial Analysis:**
- Average family spends: $12,000/year on groceries, $3,000 on dining
- 5% grocery savings = $600/year
- Kids eat free 2x/month = $480/year savings
- Total value: ~$1,500/year vs $139 cost

**Pros:**
- Massive value for price-sensitive families
- Creates daily engagement touchpoints
- Differentiates from shipping-focused competitors

**Cons:**
- Complex partnerships needed
- Operational complexity
- May not appeal to non-families

#### Solution 3: 10X - Prime Community Co-op
**What:** Revolutionary group-buying membership model
**Key Features:**
- **Neighborhood Pods**: 5-10 families share one Prime membership
- **Bulk Buying Power**: Unlock wholesale prices with group orders
- **Community Delivery Hub**: One delivery point reduces costs
- **Shared Digital Benefits**: Rotate Prime Video profiles
- **Social Features**: Neighborhood recommendations, lending library
- **Progressive Pricing**: $20-50/year per family based on usage

**Network Effects:**
- More pods = better bulk pricing
- Social pressure to maintain membership
- Community building in neighborhoods

**Pros:**
- Makes Prime accessible to any income level
- Creates powerful network effects
- Builds Amazon deeper into communities

**Cons:**
- Completely new operational model
- Complex logistics
- Potential for membership sharing abuse

---

## Recommendation: Prime Family Savings Hub

### Why This Solution:

1. **Addresses Root Cause**
   - Price-sensitive customers care about total savings, not shipping
   - $1,500 value >> $139 cost makes decision obvious
   - Tangible, daily value beyond e-commerce

2. **Competitive Differentiation**
   - Walmart+ can copy shipping, can't easily copy restaurant network
   - Creates switching costs through family routines
   - Platform approach vs feature approach

3. **Business Model Fit**
   - Leverages Amazon's scale for partner negotiations
   - Data from savings hub improves ad targeting
   - Opens new revenue streams (partner fees)

### Implementation Approach:

**Phase 1 (Q1-Q2): Foundation**
- Grocery price matching in 10 test markets
- Sign 1,000 restaurant partners
- Build Rx partnership with CVS/Walgreens
- MVP of utility optimizer

**Phase 2 (Q3-Q4): Scale**
- National grocery rollout
- 10,000 restaurant partners
- Add school supplies subscription
- Marketing campaign: "Prime Saves Families $1,500/year"

**Phase 3 (Year 2): Optimize**
- AI-powered savings recommendations
- Premium tier with concierge service
- B2B2C partnerships with employers

### Go-to-Market:

1. **Messaging Strategy**
   - Lead with savings calculator showing personal value
   - "Prime: Now More Than Shipping"
   - Customer testimonials: "Saved $2,000 last year"

2. **Acquisition Channels**
   - School partnerships (reach parents)
   - Employer benefits programs
   - Community organization partnerships

3. **Trial Strategy**
   - 3-month free trial (vs current 1 month)
   - Show running savings tally in app
   - Gamify savings achievements

### Financial Projections:

**Year 1:**
- New members: 12M (exceed 10M target)
- Trial conversion: 80%
- Revenue impact: +$1.7B
- Partner revenue: $200M
- Implementation cost: $500M
- Net impact: +$1.4B

**Key Assumptions:**
- 30% of price-sensitive segment converts
- $30 CAC through targeted marketing
- 15% commission on partner savings

### Success Metrics & Tracking:

1. **Acquisition Metrics**
   - Weekly new Prime members by source
   - Trial-to-paid conversion by feature usage
   - CAC by channel

2. **Engagement Metrics**
   - Monthly active savings features users
   - Average savings per member
   - Cross-feature adoption rate

3. **Retention Metrics**
   - Cohort retention by primary feature used
   - Lifetime value by acquisition source
   - Churn prediction scores

### Risks & Mitigation:

1. **Partner Execution Risk**
   - Mitigation: Start with proven partners, phased rollout
   - Backup: Direct Amazon offerings if partners fail

2. **Margin Pressure**
   - Mitigation: Partner-funded discounts
   - Backup: Adjust savings percentages by category

3. **Complexity Overwhelming Users**
   - Mitigation: Smart defaults, simple onboarding
   - Backup: Segment features by user type

---

## Why This Beats Traditional Approaches:

1. **Reframes the Value Prop**: From "fast shipping" to "family CFO"
2. **Expands TAM**: Makes Prime relevant to non-shoppers
3. **Platform vs Feature**: Creates ecosystem partners can build on
4. **Measurable Daily Value**: Savings tracker shows ROI constantly
5. **Social Proof at Scale**: Neighbors discussing savings creates FOMO

This transforms Prime from a shipping program into an essential family financial service, making the $139 fee feel like the best investment a family can make. 