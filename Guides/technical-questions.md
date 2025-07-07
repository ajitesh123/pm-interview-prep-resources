# Technical Questions - PM Interview Guide

## Overview
Technical interviews are important at tech firms like Google, Twilio, and startups. While you don't need to be exceptional, you must demonstrate basic technical competence to build credibility with engineering teams.

## What They Test
- Basic software development knowledge
- Ability to participate in technical design discussions
- Understanding of trade-offs in technical decisions
- Capability to translate customer problems into technical requirements
- Credibility as a technical peer to engineers

## Four Main Categories

### 1. Experience-Based Questions
Ice-breaker questions about your technical background.

**Examples:**
- "Tell me about a time you worked with engineers on a technical challenge"
- "Describe a technical trade-off decision you made"
- "Walk me through the technical architecture of your last product"

**Tips:**
- Focus on your contribution to technical discussions
- Highlight how you influenced technical decisions
- Show you can learn technical concepts on the job

### 2. System Design Questions
Most popular type - tests high-level technical thinking.

**Common questions:**
- Design a pastebin
- Design a web crawler
- Design a chat application
- Design Twitter timeline
- Design Uber
- Design a URL shortener

**Approach:**
1. Clarify requirements (≤3 key requirements)
2. Define system interface (APIs) and data model
3. Draw high-level architecture
4. Walk through how requirements are met
5. Deep dive where interviewer directs

### 3. Algorithm Questions
Rarely involve actual coding, focus on approach.

**Common topics:**
- Reverse a linked list
- String manipulation
- Array operations
- Basic graph traversal
- Sorting algorithms

**Key concepts to know:**
- Big O notation
- Basic data structures (arrays, linked lists, trees, graphs)
- Common algorithms (binary search, DFS/BFS)
- Recursion basics

### 4. Technology 101 Questions
General questions about how technology works.

**Examples:**
- "What happens when you type google.com?"
- "How does the internet work?"
- "How do you optimize page load time?"
- "Explain cloud computing"
- "How does voice assistant work?"

## System Design Deep Dive

### Core Components to Know

**1. Client-Server Architecture**
- Request-response model
- REST APIs
- Websockets for real-time
- Server-sent events

**2. Load Balancing**
- Round robin
- Least connections
- Geographic routing
- Health checks

**3. Databases**
- SQL vs NoSQL trade-offs
- CAP theorem
- Sharding strategies
- Replication for availability

**4. Caching**
- Client-side vs server-side
- Cache invalidation strategies
- CDNs for static content
- Redis for dynamic data

**5. Message Queues**
- Pub/sub patterns
- Apache Kafka
- Asynchronous processing
- Event-driven architecture

**6. Storage**
- Object storage (S3)
- File systems
- Distributed storage
- Data lakes

### Sample System Design Answer

**Question**: "Design a web crawler"

**Answer structure**:

1. **Requirements**:
   - Crawl 1B pages/month
   - Store pages for 5 years
   - Handle duplicates

2. **High-level design**:
   ```
   URL Frontier → Fetcher → Parser → Storage
        ↑                      ↓
        ← URL Extractor ← Deduplication
   ```

3. **Key components**:
   - URL Frontier: Priority queue for URLs
   - Fetcher: Downloads pages, respects robots.txt
   - Parser: Extracts content and links
   - Deduplication: Prevents duplicate crawling
   - Storage: Distributed file system

4. **Scale considerations**:
   - Distributed crawling
   - DNS caching
   - Politeness policies
   - Geographic distribution

## Algorithm Interview Tips

### Think Aloud Process
1. Understand the problem
2. Work through examples
3. State the approach
4. Discuss time/space complexity
5. Consider edge cases

### Must-Know Concepts
- **Arrays**: Indexing, searching, sorting
- **Strings**: Manipulation, pattern matching
- **Trees**: Traversal, balanced trees
- **Graphs**: BFS/DFS, shortest path
- **Hash tables**: O(1) lookup
- **Recursion**: Base cases, stack overflow

## Technology 101 Key Points

### "What happens when you type a URL?"
1. DNS lookup (domain → IP)
2. TCP connection established
3. HTTP request sent
4. Server processes request
5. Response sent back
6. Browser renders page

### Cloud Computing Basics
- **IaaS**: Infrastructure (AWS EC2)
- **PaaS**: Platform (Google App Engine)
- **SaaS**: Software (Salesforce)
- **Serverless**: Functions (Lambda)
- **Containers**: Docker, Kubernetes

### Modern Tech Concepts
- **Microservices**: Small, independent services
- **API Gateway**: Central entry point
- **Service Mesh**: Inter-service communication
- **CI/CD**: Automated deployment
- **Observability**: Monitoring, logging, tracing

## Common Mistakes to Avoid
- Going too deep technically (you're not the engineer)
- Not clarifying requirements first
- Ignoring trade-offs
- Forgetting about scale
- Not considering failure scenarios

## Collaboration with Engineering

### How to Show PM-Eng Partnership
- Ask about technical constraints
- Propose multiple options with trade-offs
- Focus on customer requirements
- Defer deep implementation to engineers
- Show willingness to learn

### Key Phrases
- "I'd work with engineering to determine..."
- "The trade-off here would be..."
- "From a customer perspective, we need..."
- "What are the technical constraints?"

## AI Practice Scenarios
- [Web Crawler System Design](https://app.toughtongueai.com/run/system-design-interview-web-crawler-676a42c0ae833c968b618f1b/)

## Preparation Resources
- System Design Primer (GitHub)
- High Scalability blog
- Engineering blogs (Uber, Airbnb, Netflix)
- CS50 Harvard (basics)
- LeetCode (algorithm practice)

## Quick Reference Sheet

### Latency Numbers
- L1 cache: 0.5 ns
- L2 cache: 7 ns
- RAM: 100 ns
- SSD: 150 μs
- Network: 150 ms
- HDD: 10 ms

### Capacity Planning
- 1 server: ~1000 QPS
- 1 GB RAM: ~1M cache entries
- 1 TB storage: ~1B records

Remember: Focus on high-level design and customer impact, not implementation details. Show you can be a technical partner, not a replacement engineer. 