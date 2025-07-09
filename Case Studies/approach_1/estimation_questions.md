# Estimation Questions

## Question Type: Analytical Questions

Estimation questions test your ability to make reasonable assumptions, break down complex problems, and arrive at logical conclusions with limited information - key skills for product managers who must make decisions with incomplete data.

---

## Question 1: Estimate McDonald's Revenue

**Question:** Estimate McDonald's annual revenue in the United States.

### Solution Framework

#### 1. Clarify Requirements
- **Scope:** US only (not global)
- **Time period:** Annual revenue
- **Include:** All revenue streams (food, drinks, franchising)

#### 2. Break Down the Problem

**Approach:** Number of restaurants × Average revenue per restaurant

#### 3. Estimate Components

**Number of McDonald's Restaurants in US:**
- US population: ~330 million
- Assume 1 McDonald's per 10,000 people (reasonable for fast food penetration)
- Estimated restaurants: 33,000

**Revenue per Restaurant:**
- **Customers per day per restaurant:** 1,000 (mix of breakfast, lunch, dinner)
- **Average transaction value:** $8 (meal combos, individual items)
- **Daily revenue per restaurant:** 1,000 × $8 = $8,000
- **Annual revenue per restaurant:** $8,000 × 365 = $2.9 million

#### 4. Calculate Total Revenue
**Total US Revenue:** 33,000 restaurants × $2.9 million = $96 billion

#### 5. Sanity Check
- McDonald's is one of largest fast food chains globally
- $96B seems reasonable for massive US operations
- Compare to total US restaurant industry (~$800B) - roughly 12% seems high but McDonald's is dominant

#### 6. Uncertainties and Refinements
- **Location variance:** Urban vs. rural restaurant performance
- **Franchise fees:** Corporate-owned vs. franchised revenue recognition
- **Seasonal fluctuations:** Holiday periods, summer variations
- **Competition impact:** Market saturation effects

**Refined estimate:** $60-80 billion (accounting for location variance and franchise model)

---

## Question 2: Gmail Queries Per Second

**Question:** How many queries per second does Gmail get?

### Solution Framework

#### 1. Clarify Requirements
- **Queries:** Include all Gmail operations (read, send, search, login)
- **Time period:** Average QPS across a year
- **Scope:** Global Gmail usage

#### 2. Break Down the Problem

**Approach:** Total users × Queries per user per day ÷ Seconds per day

#### 3. Estimate Components

**Gmail User Base:**
- Google has 1+ billion Gmail users globally
- Active users (use Gmail at least monthly): ~800 million
- Daily active users: ~400 million

**Queries per User per Day:**
- **Typical office worker:** Checks email 20 times/day, sends 10 emails
- **Casual user:** Checks 5 times/day, sends 2 emails
- **Heavy user:** Checks 50 times/day, sends 20 emails

**User Distribution:**
- Heavy users (10%): 40 million × 70 queries = 2.8B queries
- Office workers (30%): 120 million × 30 queries = 3.6B queries
- Casual users (60%): 240 million × 7 queries = 1.7B queries

**Total daily queries:** 8.1 billion

#### 4. Calculate QPS
**Average QPS:** 8.1 billion ÷ 86,400 seconds = ~94,000 QPS

#### 5. Peak vs. Average Considerations
- **Time zone distribution:** Global usage creates more consistent load
- **Business hours impact:** 2-3x spike during business hours
- **Peak QPS estimate:** 200,000-300,000 QPS

#### 6. Sanity Check
- Google Search handles millions of QPS
- Gmail having ~100K QPS seems reasonable for 400M daily users
- Comparable to other major web services

---

## Question 3: iPhone Sales in US Per Year

**Question:** How many iPhones are sold in the US each year?

### Solution Framework

#### 1. Clarify Requirements
- **Scope:** US market only
- **Time period:** Annual sales
- **Include:** All iPhone models (new releases, older models)

#### 2. Break Down the Problem

**Approach:** Market size × Market penetration × Replacement rate

#### 3. Estimate Components

**US Smartphone Market:**
- US population: 330 million
- Smartphone penetration: 85% = 280 million smartphone users
- Average replacement cycle: 2.5-3 years

**iPhone Market Share:**
- US iPhone market share: ~50% (consistently higher than global)
- iPhone users in US: 140 million

**Replacement and Growth:**
- **Existing user replacement:** 140M ÷ 2.5 years = 56M/year
- **New smartphone adoptions:** 5M/year (population growth, young users)
- **Android to iPhone switches:** 5M/year (net positive for iPhone)
- **Additional devices:** 4M/year (business phones, gifts, multiple devices)

#### 4. Calculate Total Sales
**Annual iPhone sales:** 56M + 5M + 5M + 4M = 70 million iPhones

#### 5. Sanity Check
- Apple reports ~200M iPhones sold globally per year
- US being ~35% of global sales (70M/200M) aligns with economic share
- Average selling price $800 × 70M = $56B revenue (reasonable for Apple's size)

#### 6. Market Dynamics
- **New model years:** Higher sales in Q4 with new releases
- **Economic factors:** Recession impact on premium phone sales
- **5G adoption:** Technology transitions drive replacement cycles
- **Trade-in programs:** Accelerate upgrade cycles

**Refined estimate:** 65-75 million iPhones annually

---

## Question 4: Cost to Run Flickr for 20GB User

**Question:** Estimate how much it costs to run Flickr for a user with 20GB of photos.

### Solution Framework

#### 1. Clarify Requirements
- **User type:** 20GB storage user (heavy user)
- **Costs:** Infrastructure, bandwidth, processing
- **Time period:** Annual cost per user

#### 2. Break Down the Problem

**Cost Components:**
1. Storage costs
2. Bandwidth costs  
3. Processing costs (thumbnails, metadata)
4. General infrastructure overhead

#### 3. Estimate Component Costs

**Storage Costs:**
- **Raw storage:** 20GB × $0.02/GB/month = $0.40/month
- **Redundancy (3x):** $0.40 × 3 = $1.20/month
- **Annual storage cost:** $1.20 × 12 = $14.40/year

**Bandwidth Costs:**
- **Upload traffic:** 20GB initial + 2GB annual additions = 22GB upload
- **Download traffic:** Assume 2x storage viewed annually = 40GB
- **CDN costs:** 62GB × $0.05/GB = $3.10/year

**Processing Costs:**
- **Thumbnail generation:** 20GB ÷ 3MB avg = ~6,700 photos
- **Processing cost:** 6,700 photos × $0.001 = $6.70 one-time
- **Metadata/search indexing:** $2/year

**Infrastructure Overhead:**
- **Servers, networking, facilities:** $5/user/year (amortized)
- **Support and operations:** $3/user/year

#### 4. Calculate Total Cost
**Annual cost per 20GB user:**
- Storage: $14.40
- Bandwidth: $3.10  
- Processing: $2.00 (amortized)
- Infrastructure: $8.00
- **Total: ~$27.50/year**

#### 5. Revenue Comparison
- **Flickr Pro subscription:** ~$50/year
- **Cost margin:** $50 - $27.50 = $22.50 profit margin (45%)
- Reasonable margin for sustainable business

#### 6. Scale Efficiencies
- **Storage costs decrease** with scale (enterprise pricing)
- **CDN costs improve** with volume commitments
- **Processing costs amortized** across user base
- **At scale estimate:** $15-20/year per 20GB user

---

## Question 5: Elevators for 50-Story Building

**Question:** How many elevators do you need for a 50-story building?

### Solution Framework

#### 1. Clarify Requirements
- **Building type:** Office building (not residential)
- **Occupancy:** Standard office density
- **Service level:** Reasonable wait times during peak hours

#### 2. Break Down the Problem

**Approach:** Calculate peak demand and elevator capacity to determine optimal number

#### 3. Estimate Building Parameters

**Building Occupancy:**
- **Floor space:** 20,000 sq ft per floor (typical office building)
- **Usable space:** 80% (corridors, bathrooms, mechanical)
- **Office density:** 200 sq ft per person
- **People per floor:** 16,000 × 80% ÷ 200 = 64 people/floor
- **Total building occupancy:** 50 floors × 64 = 3,200 people

**Peak Traffic Patterns:**
- **Morning rush:** 50% arrive within 30 minutes (1,600 people)
- **Lunch time:** 25% leave/return within 15 minutes (800 people)
- **Evening rush:** 60% leave within 45 minutes (1,920 people)

#### 4. Elevator Performance Analysis

**Single Elevator Capacity:**
- **Car capacity:** 15 people
- **Travel time:** 2 seconds per floor + 10 seconds loading/unloading
- **Round trip time (ground to floor 25 avg):** 50 seconds + 20 seconds = 70 seconds
- **Trips per hour:** 3,600 ÷ 70 = 51 trips
- **People per hour:** 51 × 15 = 765 people/hour

#### 5. Calculate Required Elevators

**Peak Hour Demand (Morning Rush):**
- **People to transport:** 1,600 people in 30 minutes
- **Required capacity:** 1,600 ÷ 0.5 hours = 3,200 people/hour
- **Elevators needed:** 3,200 ÷ 765 = 4.2 → 5 elevators (minimum)

**Service Quality Considerations:**
- **Wait time target:** <30 seconds during peak
- **Redundancy:** 1 elevator for maintenance/backup
- **Express service:** Consider express elevators to top floors

#### 6. Final Recommendation

**Optimal Configuration:**
- **6-8 total elevators** for 50-story building
- **Possible layout:** 
  - 4 elevators serving floors 1-25
  - 4 elevators serving floors 26-50
  - Express elevators for top floors

**Alternative Configurations:**
- **High-speed elevators:** Fewer elevators with better performance
- **Destination dispatch:** Advanced control systems improve efficiency
- **Freight elevators:** Separate elevators for goods/service

#### 7. Industry Benchmarks
- **Rule of thumb:** 1 elevator per 40-60 occupants in high-rise
- **3,200 occupants ÷ 50 = 64 elevators** (way too many)
- **Refined rule:** 1 elevator per 400-600 people for office buildings
- **Industry standard:** 5-8 elevators for 50-story office building

**Final answer: 6-8 elevators** depending on specific performance requirements and building layout.

---

## Key Estimation Success Factors

### General Approach
1. **Ask clarifying questions** to define scope precisely
2. **Break down** complex problems into manageable components  
3. **Use round numbers** to simplify calculations
4. **Leverage benchmarks** and real-world analogies
5. **Perform sanity checks** against known data points
6. **Acknowledge uncertainties** and key assumptions

### Common Techniques
- **Top-down vs. bottom-up** estimation approaches
- **Triangulation** using multiple methods
- **Order of magnitude** thinking
- **Proxy metrics** when direct data unavailable
- **Sensitivity analysis** for key variables

### Communication Tips
- **Show your work** - explain reasoning clearly
- **State assumptions** explicitly
- **Discuss trade-offs** and alternative approaches
- **Provide ranges** rather than precise numbers
- **Connect to business impact** when relevant