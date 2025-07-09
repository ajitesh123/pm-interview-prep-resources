# Estimation Questions - Comprehensive Guide

## Overview
Estimation questions test your ability to break down complex problems, make reasonable assumptions, and perform mental math. This guide covers all 5 estimation questions from DECODE & CONQUER with modern frameworks and detailed approaches.

---

## General Framework for Estimation

### The ESTIMATE Method™

**E** - Establish the scope and clarify
**S** - State your approach (top-down or bottom-up)
**T** - Think through the components
**I** - Identify key assumptions
**M** - Make calculations (show your work)
**A** - Adjust for reasonableness
**T** - Test with sanity checks
**E** - Explain your final answer

### Key Principles

1. **Round Numbers Aggressively**: 314M → 300M, 365 days → 360 days
2. **State Assumptions Clearly**: "I assume that..."
3. **Show Your Work**: Write/speak through calculations
4. **Sanity Check**: Compare to known benchmarks
5. **Be Comfortable with Uncertainty**: ±20% is fine

---

# Question 1: Estimate McDonald's Revenue

## Approach: Bottom-Up (Store Level)

### Step 1: Clarify (30 seconds)
"Are we looking at:
- Global or US revenue? → *Global*
- Annual revenue? → *Yes*
- Just restaurants or including franchising fees? → *All revenue*

### Step 2: Structure the Calculation

```
Global Revenue = US Revenue + International Revenue
US Revenue = # of Stores × Revenue per Store
International Revenue = US Revenue × International Multiplier
```

### Step 3: Calculate US Store Revenue

**Peak Hours Analysis (8am-8pm = 12 hours)**
- Breakfast (8am-11am): 100 customers/hour × 3 hours = 300
- Lunch (11am-2pm): 150 customers/hour × 3 hours = 450
- Dinner (5pm-8pm): 120 customers/hour × 3 hours = 360
- Other peak hours: 80 customers/hour × 3 hours = 240
- **Total peak customers**: 1,350

**Off-Peak Hours (12 hours)**
- Average: 30 customers/hour × 12 hours = 360

**Daily Total**: 1,350 + 360 = 1,710 customers
*Round to 1,700 for easier math*

**Average Transaction Value**
- Breakfast: $6 (coffee + sandwich)
- Lunch/Dinner: $9 (meal combo)
- Weighted average: $8

**Daily Revenue**: 1,700 × $8 = $13,600
**Annual Revenue per Store**: $13,600 × 365 ≈ $5M

### Step 4: Number of US Stores

**Method 1: City-Based**
- US Population: 330M → 300M
- Average city size: 60K people
- Number of cities: 300M ÷ 60K = 5,000
- McDonald's per city: 3 (average)
- **Total**: 15,000 stores

**Method 2: Per Capita**
- 1 McDonald's per 20,000 people
- 300M ÷ 20K = 15,000 stores

*Conclusion: 15,000 US stores*

### Step 5: Calculate Total Revenue

**US Revenue**: 15,000 stores × $5M = $75B

**International Revenue**:
- McDonald's operates in ~100 countries
- US represents ~40% of global revenue
- Global = US ÷ 0.4 = $75B ÷ 0.4 = $187.5B

**Round to $180-200B**

### Step 6: Sanity Check

**Check 1: Revenue per Person**
- Global population: 8B
- McDonald's revenue: $180B
- Per person: $180B ÷ 8B = $22.50/year
- *Reasonable for developed countries*

**Check 2: Market Share**
- Global fast food market: ~$800B
- McDonald's share: $180B ÷ $800B = 22.5%
- *Reasonable for market leader*

### Alternative Approach: Top-Down

```
Global Population: 8B
Addressable Market (can afford): 3B (37.5%)
McDonald's Customers: 1B (33% of addressable)
Visits per Year: 20 (monthly-ish)
Average Spend: $8
Revenue = 1B × 20 × $8 = $160B
```

### Interview Answer Template

"I'll estimate McDonald's global annual revenue using a bottom-up approach, starting with a single store.

For a typical McDonald's:
- Peak hours (12h): 110 customers/hour = 1,320 customers
- Off-peak (12h): 30 customers/hour = 360 customers  
- Daily total: ~1,700 customers at $8 average = $13,600
- Annual: ~$5M per store

For number of stores:
- US has ~300M people, 1 McDonald's per 20K people = 15,000 stores
- US revenue: 15,000 × $5M = $75B

Globally:
- McDonald's in ~100 countries
- US is ~40% of revenue
- Global revenue = $75B ÷ 0.4 = ~$180B

To sanity check: That's ~$22 per person globally, which seems reasonable given McDonald's presence."

**Actual Answer: ~$23B (2022)**
*Note: Our estimate is high because we overestimated revenue per store*

---

# Question 2: Gmail Queries Per Second

## Approach: User-Based Calculation

### Step 1: Clarify
"When we say 'query', do we mean:
- Any Gmail operation (read, write, search)? → *Yes*
- Including automated/background queries? → *No, just user-initiated*
- Global or specific region? → *Global*

### Step 2: Structure

```
Queries/Second = Total Daily Queries ÷ Seconds per Day
Total Daily Queries = Active Users × Queries per User per Day
```

### Step 3: Calculate Active Gmail Users

**Total Internet Users**
- Global population: 8B
- Internet penetration: 60% (higher in developed, lower in developing)
- Internet users: 8B × 0.6 = 4.8B

**Gmail Market Share**
- Major providers: Gmail, Outlook, Yahoo, others
- Gmail dominance: ~30% globally
- Gmail users: 4.8B × 0.3 = 1.44B
- *Round to 1.5B*

**Daily Active Users**
- Not everyone checks daily
- DAU/MAU ratio: 40% (lower than social media)
- Daily active: 1.5B × 0.4 = 600M

### Step 4: Queries per User

**Typical User Behavior**
- Check email: 4 times/day
- Actions per session:
  - Load inbox: 1 query
  - Read emails: 5 queries (click 5 emails)
  - Write/reply: 1 query
  - Search: 0.5 queries (not every session)
  - Delete/archive: 2 queries
- **Total per session**: 9.5 ≈ 10 queries
- **Daily queries**: 4 sessions × 10 = 40 queries/user

### Step 5: Calculate Total

**Total Daily Queries**
- 600M users × 40 queries = 24B queries/day

**Queries Per Second**
- Seconds per day: 24 × 60 × 60 = 86,400 ≈ 90,000
- Queries per second: 24B ÷ 90K = 267K
- **Round to 250-300K QPS**

### Step 6: Adjust for Peak Hours

**Time Zone Distribution**
- Not uniform - peak hours create 3-4x normal load
- Average QPS: 267K
- Peak QPS: 267K × 3 = ~800K

### Alternative Approach: Infrastructure-Based

```
Google's data centers: ~20 major ones
Servers per data center: ~1M
Total servers: 20M
Gmail's share: 5% = 1M servers
Queries per server: 1 QPS (conservative)
Total: 1M QPS
```

### Sanity Checks

1. **Compare to Google Search**
   - Google Search: ~100K QPS
   - Gmail involves more operations per user
   - 250K QPS seems reasonable

2. **Infrastructure Cost**
   - At 250K QPS, need ~250K cores
   - Cost: ~$50M/year in servers
   - Reasonable for Google's scale

### Interview Answer

"I'll estimate Gmail's queries per second by calculating daily active users and their behavior.

Starting with users:
- Global internet users: ~5B
- Gmail's market share: ~30% = 1.5B accounts  
- Daily active users: ~40% = 600M

User behavior:
- Average user checks 4 times daily
- Each session: ~10 queries (read, write, search)
- Total: 40 queries per user per day

Calculation:
- Daily queries: 600M × 40 = 24B
- Seconds per day: ~90,000
- Average QPS: 24B ÷ 90K ≈ 270K

Accounting for peak hours (3x average): ~800K QPS peak

This aligns with Gmail being more query-intensive than search but within Google's infrastructure capabilities."

---

# Question 3: iPhones Sold in US Annually

## Approach: Market-Based Analysis

### Step 1: Clarify
- New iPhones only or including used? → *New only*
- Retail or including corporate sales? → *All sales*
- Calendar year or fiscal year? → *Calendar year*

### Step 2: Structure

```
Annual iPhone Sales = Replacement Cycle + New Users + Switchers
```

### Step 3: Calculate Addressable Market

**US Smartphone Users**
- US Population: 330M
- Smartphone penetration by age:
  - 0-12 years (15% of pop): 10% have phones = 5M
  - 13-17 years (5% of pop): 90% have phones = 15M
  - 18-65 years (60% of pop): 95% have phones = 190M
  - 65+ years (20% of pop): 70% have phones = 45M
- **Total smartphone users**: 255M

### Step 4: iPhone Market Share

**Current Market Share**
- iPhone vs Android in US: Roughly 55/45 split
- iPhone users: 255M × 0.55 = 140M

### Step 5: Calculate Annual Sales

**A. Replacement Purchases**
- Average replacement cycle: 3 years
- Annual replacements: 140M ÷ 3 = 47M

**B. New iPhone Users**
- Young people getting first phone: 5M/year
- iPhone's share of new users: 60% = 3M

**C. Android Switchers**
- Android users: 115M
- Annual switch rate: 5%
- Switchers: 115M × 0.05 = 6M

**Total Annual Sales**: 47M + 3M + 6M = 56M

### Step 6: Seasonality Adjustment

**Quarterly Distribution**
- Q1 (Jan-Mar): 20%
- Q2 (Apr-Jun): 15%
- Q3 (Jul-Sep): 20%
- Q4 (Oct-Dec): 45% (new iPhone launch)

### Alternative Approach: Revenue-Based

```
Apple's US Revenue: ~$150B
iPhone share of revenue: 50% = $75B
Average iPhone price: $900
Units sold: $75B ÷ $900 = 83M
(This includes iPads miscategorized, so reduce by 30%)
Adjusted: 58M iPhones
```

### Sanity Checks

1. **Per Capita Check**
   - 56M phones ÷ 330M people = 17%
   - Reasonable given 3-year cycle

2. **Market Value Check**
   - 56M × $900 = $50B
   - Apple's US iPhone revenue ≈ $50-60B ✓

### Interview Answer

"I'll estimate annual iPhone sales in the US by analyzing the replacement cycle and new users.

Starting with the market:
- US population: 330M
- Smartphone users: ~255M (varies by age group)
- iPhone's US market share: ~55% = 140M iPhone users

Annual sales components:
1. Replacements: 140M ÷ 3-year cycle = 47M
2. First-time smartphone users: 5M youth × 60% iPhone share = 3M
3. Android switchers: 115M Android × 5% switch rate = 6M

Total: 47M + 3M + 6M = 56M iPhones annually

This represents ~$50B in revenue at $900 average price, which aligns with Apple's reported US iPhone revenue."

**Actual: ~75-80M units (includes some iPads in reports)**

---

# Question 4: Cost to Run Flickr for 20GB User

## Approach: Cost Component Analysis

### Step 1: Clarify
- Actual usage or allocated capacity? → *Actual usage*
- Including bandwidth or just storage? → *All costs*
- Time period? → *Monthly cost*

### Step 2: Structure

```
Total Cost = Storage + Bandwidth + Compute + Operations
```

### Step 3: User Behavior Analysis

**Typical 20GB Plan User**
- Plan: 20GB allowed
- Actual usage: 30% = 6GB (most don't max out)
- Growth rate: 100MB/month

**Photo Characteristics**
- Average photo: 5MB (high-res)
- Total photos: 6GB ÷ 5MB = 1,200 photos
- Upload pattern: 50 photos/month

### Step 4: Calculate Costs

**A. Storage Costs**
```
Primary Storage: 6GB × $0.10/GB = $0.60
Backup (2x redundancy): 6GB × $0.10/GB = $0.60
CDN Cache: 1GB hot data × $0.20/GB = $0.20
Total Storage: $1.40/month
```

**B. Bandwidth Costs**
```
Photo Views:
- 20% of photos viewed monthly = 240 photos
- Thumbnail (200KB): 240 × 0.2MB = 48MB
- Full size (2MB compressed): 20 photos × 2MB = 40MB
- Total bandwidth: 88MB ≈ 0.1GB

Cost: 0.1GB × $0.50/GB = $0.05/month
```

**C. Compute Costs**
```
Image Processing:
- Upload processing: 50 photos × 0.1 CPU-sec = 5 CPU-sec
- Thumbnail generation: 50 × 0.05 CPU-sec = 2.5 CPU-sec
- Total: 7.5 CPU-sec/month

Cost: 7.5 × $0.00001/CPU-sec = $0.00075 ≈ $0.01/month
```

**D. Operational Overhead**
```
- Database entries
- Metadata storage  
- API calls
- Monitoring

Estimated: $0.10/user/month
```

**Total Cost**: $1.40 + $0.05 + $0.01 + $0.10 = **$1.56/month**

### Step 5: Scale Considerations

**Cost Reductions at Scale**
- Bulk storage rates: -30%
- Deduplication: -20%
- Efficient CDN usage: -10%

**Scaled Cost**: $1.56 × 0.4 = $0.62/month

### Alternative Approach: AWS Pricing

```
S3 Storage: 6GB × $0.023/GB = $0.14
S3 Requests: 1000 × $0.0004 = $0.40
CloudFront: 0.1GB × $0.085/GB = $0.01
Lambda: Minimal = $0.01
Total AWS: $0.56/month
```

### Interview Answer

"I'll calculate the monthly cost to run Flickr for a 20GB user by analyzing storage, bandwidth, and compute costs.

First, user behavior:
- 20GB plan but typical usage is 30% = 6GB
- About 1,200 photos at 5MB each
- Uploads 50 photos/month

Cost breakdown:
1. **Storage**: 6GB primary + backup = $1.40
2. **Bandwidth**: 0.1GB for viewing = $0.05
3. **Compute**: Image processing = $0.01
4. **Operations**: Overhead = $0.10

Total: ~$1.56/month per user

At Flickr's scale with deduplication and bulk rates, this could reduce to $0.60-0.80/month, explaining how they can offer the service profitably at their price point."

---

# Question 5: Elevators for 50-Story Building

## Approach: Demand-Capacity Analysis

### Step 1: Clarify
- Building type? → *Office building*
- Location? → *Major city downtown*
- Budget constraints? → *Standard commercial*

### Step 2: Structure

```
Elevators Needed = Peak Demand ÷ Elevator Capacity
Peak Demand = People to Move ÷ Time Window
Elevator Capacity = Trips per Hour × People per Trip
```

### Step 3: Building Analysis

**Building Specifications**
- 50 floors (assume ground floor + 49 office floors)
- Floor area: 20,000 sq ft per floor
- Usable space: 80% = 16,000 sq ft
- People per floor: 16,000 ÷ 150 sq ft/person = 107
- Round to 100 people/floor
- **Total building population**: 49 floors × 100 = 4,900 people

### Step 4: Peak Hour Analysis

**Morning Rush (8-9 AM)**
- Arrival pattern: 80% arrive in this hour
- People to move: 4,900 × 0.8 = 3,920
- Peak 15 minutes: 40% = 1,568 people

**Elevator Wait Time Standard**
- Industry standard: 30-second average wait
- Implies serving everyone in 2-3 minutes

### Step 5: Elevator Capacity

**Single Elevator Performance**
- Capacity: 15 people
- Average trip:
  - Load time: 30 seconds
  - Travel time: 120 seconds (multiple stops)
  - Unload time: 30 seconds
  - Return time: 60 seconds
  - **Total cycle**: 240 seconds = 4 minutes

**Trips per Hour**: 60 min ÷ 4 min = 15 trips
**People per Hour**: 15 trips × 15 people = 225 people/elevator

### Step 6: Calculate Number Needed

**Base Calculation**
- Peak 15-min demand: 1,568 people
- Hourly equivalent: 1,568 × 4 = 6,272 people/hour
- Elevators needed: 6,272 ÷ 225 = 28 elevators

**This seems too high! Let's optimize:**

### Step 7: Optimization Strategies

**A. Express Elevators**
- 4 express elevators (serves floors 25-50)
- 4 express elevators (serves floors 1-25)
- Reduces average stops, faster cycles

**B. Zoning**
- Low zone (1-16): 4 elevators
- Mid zone (17-33): 4 elevators  
- High zone (34-50): 4 elevators
- Express to sky lobby: 2 elevators

**C. Smart Dispatching**
- Destination dispatch system
- Groups passengers by floor
- Reduces stops by 30%

**Optimized Calculation**
- Improved capacity: 225 × 1.3 = 293 people/hour
- Elevators needed: 6,272 ÷ 293 = 21 elevators
- With zoning efficiency: 21 × 0.8 = **17 elevators**

### Step 8: Final Configuration

**Recommended Setup**
- 4 low-zone elevators (floors 1-16)
- 4 mid-zone elevators (floors 17-33)
- 4 high-zone elevators (floors 34-50)
- 2 express elevators (ground to sky lobbies)
- 2 freight/service elevators
- 1 executive express elevator
- **Total: 17 elevators**

### Sanity Check

**Benchmark Comparison**
- Empire State Building (102 floors): 73 elevators
- Ratio: 73/102 = 0.72 elevators/floor
- Our building: 17/50 = 0.34 elevators/floor
- Reasonable given modern technology

### Interview Answer

"I'll calculate elevators needed for a 50-story office building by analyzing peak demand and elevator capacity.

Building analysis:
- 50 floors, ~100 people/floor = 4,900 total
- Peak hour: 80% arrive = 3,920 people
- Peak 15 minutes: 1,568 people need service

Elevator capacity:
- 15 people per car
- 4-minute round trip cycle
- 225 people/hour/elevator baseline

Initial calculation: 6,272 peak hourly demand ÷ 225 = 28 elevators

But that's too many! With optimization:
- Zoning (low/mid/high) reduces stops
- Smart dispatching adds 30% efficiency  
- New capacity: 293 people/hour/elevator

Final configuration:
- 12 zoned passenger elevators
- 2 express elevators
- 3 service/freight elevators
- **Total: 17 elevators**

This provides <30 second average wait time during peak hours while being cost-effective."

---

## Key Takeaways for Estimation Questions

### Do's
1. **State assumptions clearly** - "I assume that..."
2. **Round aggressively** - 328M → 300M
3. **Show your work** - Write/speak each step
4. **Use benchmarks** - Compare to known values
5. **Structure your approach** - Top-down or bottom-up

### Don'ts
1. **Don't panic** - It's about process, not precision
2. **Don't use complex math** - Keep it simple
3. **Don't forget units** - Always include $/GB, people/hour
4. **Don't skip sanity checks** - Always verify reasonableness
5. **Don't be silent** - Talk through your thinking

### Common Multipliers to Remember
- Seconds in a day: ~90,000
- Days in a year: ~360
- US population: ~330M → 300M
- World population: ~8B
- Internet users: ~5B
- Smartphone penetration: ~80% (US), ~60% (global)

### Closing Template

"To summarize, I estimated [X] by [approach]. My key assumptions were [A, B, C], leading to a final estimate of [Y]. This seems reasonable because [sanity check]." 