# Analytical & Metrics Questions - PM Interview Guide

## Overview
Analytics questions are common in PM interviews, either standalone or as follow-ups to product design/strategy questions. They test your ability to use data for decision-making and bring quantitative rigor to product challenges.

## What They Test
- Quantitative and analytical thinking
- Ability to break down complex problems
- Data-driven decision making
- Understanding of metrics and experimentation
- Comfort with ambiguity and estimation

## Three Main Types

### 1. Estimation Questions
Test your ability to make product decisions with limited information.

**Common formats:**
- Market sizing: "Estimate the market size for Nvidia GPUs"
- Capacity planning: "Estimate storage needed for Google Photos"
- Revenue estimation: "Estimate Meta VR headset revenue"
- User behavior: "Estimate adoption rate for a new feature"

### 2. A/B Testing Questions
Assess your understanding of experimentation and statistical thinking.

**Key components:**
- Hypothesis formulation
- Test design and methodology
- Statistical significance understanding
- Bias awareness (novelty effect, primacy effect)

### 3. Metrics Definition
Evaluate how you measure product success.

**Common questions:**
- "What metrics would you track for Instagram ads?"
- "How would you measure community improvement in Facebook Groups?"
- "Define success metrics for a new Google Cloud product"

## Estimation Approach

### Step 1: Clarify Requirements
- Scope (geography, time frame, segments)
- What exactly needs to be estimated
- Level of precision needed

### Step 2: Break Down the Problem
**Techniques:**
- **Formula-based**: Revenue = Price × Quantity
- **Segmentation-based**: Divide by user types, geographies
- **Component-based**: Break into smaller parts
- **Geography-based**: Calculate for one region, extrapolate

### Step 3: Perform Estimation
**Key techniques:**
- **Anchoring**: Use known data points as reference
- **Proxies**: Find related, easier-to-estimate values
- **Personal reference**: Use your experience (with caution)

### Step 4: Sanity Check
- Order of magnitude verification
- Compare to related estimates
- Check against real-world constraints

### Step 5: Communicate Uncertainties
- State assumptions clearly
- Identify biggest sources of error
- Suggest how to refine with more data

## Key Numbers to Remember

### Population
- World: 8B
- US: 300M (Urban 30%, Suburban 55%, Rural 15%)
- Average US household: 3 people
- US working population: 150M

### Economy
- US GDP: $23T
- World GDP: $100T
- US median household income: $70K

### Tech/Internet
- Internet penetration: World 60%, US 90%
- Smartphone: US 80%
- iPhone market share: US 50%, World 30%
- Facebook: 3B MAU, 2B DAU

### Storage/Data
- Smartphone photo: 3MB
- 1-hour HD video: 1.5GB
- Cloud storage cost: $0.02/GB/month

## A/B Testing Framework

### 1. Define Hypotheses
- **Null hypothesis**: No difference between control and variant
- **Alternative hypothesis**: Measurable difference exists

### 2. Use PICOT Framework
- **P**opulation: Target audience
- **I**ntervention: What you're changing
- **C**omparison: Control group
- **O**utcome: Key metrics
- **T**ime: Test duration

### 3. Watch for Biases
- **Novelty effect**: Initial spike due to newness
- **Primacy effect**: Resistance to change
- **Interference**: Treatment affecting control
- **Statistical significance**: p-value < 0.05

## Metrics Framework

### Step 1: Clarify Context
- Product lifecycle stage
- Business goals
- User segments

### Step 2: Brainstorm Metrics
Map user actions to business goals:
- **Acquisition**: New users, signups
- **Engagement**: DAU/MAU, session length
- **Retention**: 7-day retention, churn rate
- **Monetization**: ARPU, conversion rate
- **Satisfaction**: NPS, CSAT

### Step 3: Select Key Metrics
- Choose 3 primary metrics
- Include 1 guardrail metric
- Balance leading and lagging indicators

### Step 4: Consider Pitfalls
- False positives/negatives
- Seasonality effects
- Selection bias
- Gaming of metrics

## Sample Estimation Answer

**Question**: "Estimate storage for Google Photos globally"

**Answer structure**:
1. **Clarify**: All photos/videos ever uploaded, including redundancy
2. **Approach**: Users × Content per user × Technical multipliers
3. **Calculate**:
   - 1.5B users globally
   - 60GB lifetime content per user
   - 3× redundancy + 25% derived data
   - = ~400 Exabytes
4. **Sanity check**: Compare to Google's infrastructure scale
5. **Uncertainties**: 4K video adoption, deletion patterns

## Common Mistakes to Avoid
- Not showing your work/assumptions
- Forgetting to sanity check
- Being too precise (false accuracy)
- Not considering edge cases
- Ignoring technical/business constraints

## AI Practice Scenarios
- [North-star Metrics](https://app.toughtongueai.com/run/pm-interviews-metrics-question-2--679a1c9aea5045dfea91233d/)
- [Google Photos Storage](https://app.toughtongueai.com/run/pm-interview-estimation-question-677e54ed261d3f3e3803b95e/)
- [YouTube CTR A/B Test](https://app.toughtongueai.com/run/pm-interview-a-b-test-679a1d29ea5045dfea91233f/)
- [Facebook Groups MAU Drop](https://app.toughtongueai.com/run/pm-interview-root-cause-analysis-question-677e5207261d3f3e3803b952/)

## Practice Tips
1. Practice mental math daily
2. Build intuition for common metrics
3. Study real A/B test case studies
4. Learn basic statistics concepts
5. Keep a notebook of useful numbers and proxies 