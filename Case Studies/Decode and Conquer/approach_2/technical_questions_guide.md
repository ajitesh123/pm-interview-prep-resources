# Technical PM Interview Questions - Comprehensive Guide

## Overview
This guide covers all 9 technical questions from the DECODE & CONQUER book with enhanced approaches based on modern best practices.

---

# Question 1: Twitter Follower Recommendation Algorithms

## Question
"Brainstorm as many algorithms as possible for recommending Twitter followers."

### Approach Framework

1. **Clarify Requirements** (1 minute)
   - One-way follow or mutual?
   - Optimize for engagement or connections?
   - Real-time or batch processing?

2. **Think in Categories** (2 minutes)
   - Graph-based algorithms
   - Content-based algorithms
   - Behavioral algorithms
   - Hybrid approaches

3. **Explain Trade-offs** (2 minutes)
   - Accuracy vs computational cost
   - Cold start problem
   - Scalability considerations

### Comprehensive Algorithm List

#### 1. Graph-Based Algorithms

**A. Friend-of-Friend (FoF)**
```
Score = Number of mutual connections
Recommend users with highest mutual connection count
```
- Pros: Simple, effective, computationally cheap
- Cons: Reinforces filter bubbles

**B. PageRank-style Authority**
```
Assign authority scores based on follower quality
Recommend high-authority users in your network vicinity
```
- Pros: Surfaces influential users
- Cons: May bias toward celebrities

**C. Community Detection**
```
1. Identify communities using Louvain algorithm
2. Recommend active members from your communities
```
- Pros: Finds topically relevant users
- Cons: Computationally intensive

**D. Triangle Closing**
```
If A→B and B→C, recommend C to A
Weight by number of such triangles
```
- Pros: Strong signal for relevance
- Cons: Limited reach

#### 2. Content-Based Algorithms

**E. Topic Modeling (LDA)**
```
1. Extract topics from user tweets
2. Match users with similar topic distributions
```
- Pros: Semantic understanding
- Cons: Language-dependent, computationally heavy

**F. Hashtag Similarity**
```
Jaccard similarity on hashtag usage
Recommend users with overlapping hashtags
```
- Pros: Simple, real-time capable
- Cons: Gameable, shallow signal

**G. Engagement Similarity**
```
Find users who like/retweet similar content
Use collaborative filtering on engagement matrix
```
- Pros: Reveals true interests
- Cons: Sparse data problem

#### 3. Behavioral Algorithms

**H. Time-based Co-occurrence**
```
Users active at similar times
Users who reply to same tweets quickly
```
- Pros: Catches real-world connections
- Cons: Time zone dependent

**I. Follow Velocity Matching**
```
Match users with similar follower growth rates
Indicates similar lifecycle stage
```
- Pros: Good for new users
- Cons: Less relevant for established users

**J. Interaction Graph Mining**
```
Build graph of @mentions, replies, quotes
Recommend based on interaction patterns
```
- Pros: Strong engagement signal
- Cons: Biased toward existing connections

#### 4. Machine Learning Approaches

**K. Deep Learning Embeddings**
```python
# Pseudo-code
user_embedding = BERT(user_tweets + profile)
recommendations = nearest_neighbors(user_embedding)
```
- Pros: Captures complex patterns
- Cons: Black box, expensive

**L. Gradient Boosted Trees**
```
Features: graph metrics + content + behavior
Target: follow probability
Use XGBoost for ranking
```
- Pros: Interpretable, powerful
- Cons: Feature engineering heavy

**M. Reinforcement Learning**
```
State: User's current following list
Action: Recommend user X
Reward: Engagement increase
```
- Pros: Optimizes long-term engagement
- Cons: Complex to implement

#### 5. Hybrid & Advanced

**N. Multi-Armed Bandit**
```
Explore: Random recommendations (10%)
Exploit: Best performing algorithm (90%)
Thompson sampling for balance
```
- Pros: Self-improving
- Cons: Needs lots of data

**O. Knowledge Graph Integration**
```
Link Twitter to Wikipedia/Freebase
Recommend based on entity relationships
```
- Pros: Rich semantic understanding
- Cons: Data integration challenges

### Recommended Implementation Strategy

**Phase 1: MVP (Month 1)**
- Friend-of-Friend (baseline)
- Hashtag similarity
- A/B testing framework

**Phase 2: Enhancement (Month 2-3)**
- Add engagement similarity
- Topic modeling
- Ensemble approach

**Phase 3: Advanced (Month 4-6)**
- Deep learning embeddings
- Multi-armed bandit optimization
- Real-time personalization

### Success Metrics
- Follow-through rate (primary)
- 7-day retention of followed users
- Engagement rate increase
- Recommendation diversity

---

# Question 2: Explain Recursion

## Question
"Explain recursion."

### Multi-Level Explanation Approach

#### Level 1: Grandmother Explanation
"Recursion is like looking into two mirrors facing each other - you see an image within an image within an image, going on seemingly forever. In programming, it's when a recipe refers to itself to solve a problem."

#### Level 2: Practical Example
"Imagine you're in a movie theater and want to know what row you're in:
1. Ask the person in front of you what row they're in
2. They ask the person in front of them
3. This continues until reaching the front row
4. The front row person says 'Row 1'
5. Each person adds 1 and tells the person behind them
6. You eventually get your answer"

#### Level 3: Technical Definition
"Recursion is a programming technique where a function calls itself to solve smaller instances of the same problem until it reaches a base case."

### Code Examples

#### Classic: Factorial
```python
def factorial(n):
    # Base case
    if n <= 1:
        return 1
    # Recursive case
    return n * factorial(n - 1)

# factorial(5) = 5 * 4 * 3 * 2 * 1 = 120
```

#### Practical: Directory Tree
```python
def count_files(directory):
    count = 0
    for item in directory.contents:
        if item.is_file():
            count += 1
        elif item.is_directory():
            # Recursive call
            count += count_files(item)
    return count
```

#### Visual: Fibonacci Tree
```
                    fib(5)
                   /      \
              fib(4)        fib(3)
             /      \      /      \
        fib(3)   fib(2) fib(2)  fib(1)
        /    \
    fib(2) fib(1)
```

### Key Concepts to Explain

1. **Base Case**: The stopping condition
   - Without it: infinite recursion → stack overflow
   - Example: `if n <= 1: return 1`

2. **Recursive Case**: The self-calling part
   - Must progress toward base case
   - Example: `return n * factorial(n-1)`

3. **Call Stack**: How computer tracks calls
   ```
   factorial(3)
   → 3 * factorial(2)
   → 3 * (2 * factorial(1))
   → 3 * (2 * 1)
   → 3 * 2
   → 6
   ```

### Common Pitfalls & Solutions

1. **Missing Base Case**
   ```python
   # BAD
   def bad_recursion(n):
       return n * bad_recursion(n-1)  # Never stops!
   
   # GOOD
   def good_recursion(n):
       if n <= 1: return 1  # Base case
       return n * good_recursion(n-1)
   ```

2. **Stack Overflow**
   ```python
   # BAD: Too deep
   def sum_to_n(n):
       if n == 0: return 0
       return n + sum_to_n(n-1)
   
   # GOOD: Tail recursion optimization
   def sum_to_n_optimized(n, acc=0):
       if n == 0: return acc
       return sum_to_n_optimized(n-1, acc+n)
   ```

### When to Use Recursion

**Good Use Cases:**
- Tree/graph traversal
- Divide-and-conquer algorithms
- Backtracking (e.g., puzzles)
- Mathematical sequences

**Avoid When:**
- Simple iteration works
- Deep recursion expected
- Performance critical

### Interview Answer Template

"Recursion is when a function calls itself to solve a problem by breaking it into smaller subproblems. 

Like Russian nesting dolls, each doll contains a smaller version of itself until you reach the tiniest doll. In recursion, we solve big problems by solving smaller versions until we reach a 'base case' - our tiniest doll.

For example, to calculate 5!, we compute 5 × 4!, which computes 4 × 3!, and so on until we reach 1! = 1. Then we multiply back up: 1 × 2 × 3 × 4 × 5 = 120.

The key is having:
1. A base case to stop recursion
2. A recursive case that makes progress toward the base case

It's powerful for problems with recursive structure like trees, but can be memory-intensive due to maintaining the call stack."

---

# Question 3: Object-Oriented Programming

## Question
"Explain object-oriented programming to your grandmother."

### Progressive Explanation Strategy

#### Analogy 1: Recipe Box
"Imagine your recipe box. Each recipe card is like an 'object' in programming:
- **The card** = Object
- **Recipe type** (dessert, main dish) = Class
- **Ingredients listed** = Properties/Attributes
- **Cooking steps** = Methods/Functions

Just like you can have multiple apple pie recipes (objects) that are all desserts (class), in programming we create multiple objects from the same class template."

#### Analogy 2: Car Factory
"Think of a car factory:
- **Blueprint** = Class (the design)
- **Actual cars** = Objects (what's built)
- **Features** (color, engine) = Properties
- **Actions** (start, stop) = Methods

The blueprint defines what all cars can do, but each car has its own specific color and license plate."

### Core OOP Concepts Explained Simply

#### 1. Classes and Objects
```python
# Class = Blueprint
class Dog:
    def __init__(self, name, breed):
        self.name = name      # Property
        self.breed = breed    # Property
    
    def bark(self):          # Method
        return f"{self.name} says Woof!"

# Objects = Actual dogs
buddy = Dog("Buddy", "Golden Retriever")
max = Dog("Max", "Beagle")
```

**Grandmother explanation**: "A class is like a cookie cutter, objects are the actual cookies. Same shape, but each can have different decorations."

#### 2. Encapsulation
```python
class BankAccount:
    def __init__(self):
        self.__balance = 0  # Private (hidden)
    
    def deposit(self, amount):  # Public method
        if amount > 0:
            self.__balance += amount
    
    def get_balance(self):  # Controlled access
        return self.__balance
```

**Grandmother explanation**: "Like a piggy bank - you can put money in and check how much is there, but you can't just reach in and grab it directly. The bank controls how you interact with your money."

#### 3. Inheritance
```python
# Parent class
class Vehicle:
    def __init__(self, wheels):
        self.wheels = wheels
    
    def move(self):
        return "Moving forward"

# Child classes
class Car(Vehicle):
    def __init__(self):
        super().__init__(4)  # Cars have 4 wheels
    
    def honk(self):
        return "Beep beep!"

class Bicycle(Vehicle):
    def __init__(self):
        super().__init__(2)  # Bikes have 2 wheels
    
    def ring_bell(self):
        return "Ring ring!"
```

**Grandmother explanation**: "Like how you inherited Grandpa's eyes and my cooking skills. A car inherits basic vehicle features but adds its own special abilities."

#### 4. Polymorphism
```python
class Cat:
    def make_sound(self):
        return "Meow"

class Dog:
    def make_sound(self):
        return "Woof"

# Same method name, different behavior
animals = [Cat(), Dog()]
for animal in animals:
    print(animal.make_sound())  # Each acts differently
```

**Grandmother explanation**: "Like how both you and your sister can 'cook dinner,' but you make pasta while she makes stir-fry. Same action, different results."

### Real-World Example: TV Remote
```python
class TVRemote:
    def __init__(self):
        self.__channel = 1      # Hidden inside
        self.__volume = 50      # Hidden inside
        self.__is_on = False    # Hidden inside
    
    # Buttons you can press (public methods)
    def power_button(self):
        self.__is_on = not self.__is_on
        return "TV On" if self.__is_on else "TV Off"
    
    def volume_up(self):
        if self.__volume < 100:
            self.__volume += 10
        return f"Volume: {self.__volume}"
    
    def change_channel(self, channel):
        if 1 <= channel <= 999:
            self.__channel = channel
        return f"Channel: {self.__channel}"

# Using the remote
my_remote = TVRemote()
print(my_remote.power_button())      # "TV On"
print(my_remote.volume_up())          # "Volume: 60"
print(my_remote.change_channel(5))    # "Channel: 5"
```

### Why OOP Matters (Business Benefits)

1. **Reusability**: Write once, use many times
   - Like using the same cookie recipe for different occasions

2. **Maintainability**: Easy to update
   - Fix the recipe card once, all future cookies improve

3. **Scalability**: Easy to extend
   - Add new frosting types without changing the cookie base

4. **Team Collaboration**: Clear organization
   - Everyone knows where to find the dessert recipes

### Common Interview Follow-ups

**Q: OOP vs Procedural Programming?**
- Procedural: Step-by-step recipe (do this, then that)
- OOP: Organized by objects and their interactions

**Q: When not to use OOP?**
- Simple scripts
- Performance-critical code
- Functional programming scenarios

**Q: Modern OOP languages?**
- Fully OOP: Java, C#, Ruby
- Multi-paradigm: Python, JavaScript, C++

---

# Question 4: Reduce Gmail Storage

## Question
"How would you reduce Gmail's storage size?"

### Structured Approach

#### 1. Understand the Problem (1 minute)
- Current scale: Billions of users, ~15GB free/user
- Cost drivers: Storage hardware, redundancy, backups
- Goal: Reduce costs while maintaining user experience

#### 2. Analyze Data Patterns
- Email types: Text, attachments, images, spam
- Usage patterns: 80% of storage from 20% of emails
- Lifecycle: Recent emails accessed more

### Solution Categories

#### Category 1: Deduplication

**A. Attachment Deduplication**
```python
# Concept
if hash(attachment) in global_storage:
    link_to_existing()
else:
    store_new_copy()
```
- Impact: 30-40% reduction (many forward same files)
- Implementation: SHA-256 hashing, reference counting
- Challenges: Privacy, deletion complexity

**B. Email Thread Deduplication**
```
Original: "Meeting at 3pm"
Reply: "Re: Meeting at 3pm [Original Message] Sounds good"

Store: Original + "Sounds good" + reference
```
- Impact: 10-15% reduction
- Implementation: Diff algorithms, thread reconstruction

**C. Cross-User Deduplication**
- Newsletter detection and single storage
- Promotional email patterns
- Impact: 20% reduction for marketing emails

#### Category 2: Compression

**A. Smart Compression**
```python
def compress_email(email):
    if email.age > 1_year:
        return heavy_compression(email)  # 10:1
    elif email.age > 1_month:
        return medium_compression(email)  # 5:1
    else:
        return light_compression(email)   # 2:1
```

**B. Format Optimization**
- Convert DOCX → Plain text with formatting
- Resize images based on viewing patterns
- Strip unnecessary metadata

#### Category 3: Intelligent Archival

**A. Hierarchical Storage**
```
Hot (SSD): Last 30 days
Warm (HDD): 30 days - 1 year  
Cold (Tape): Older than 1 year
```
- Cost: 10x cheaper for cold storage
- Trade-off: Retrieval latency

**B. Predictive Archival**
```python
archive_score = f(
    last_access_time,
    email_importance,
    user_activity_pattern,
    sender_importance
)
```

#### Category 4: User-Driven Solutions

**A. Storage Quotas with Intelligence**
- "Your storage is 90% full. Delete these 1000 emails to free 5GB?"
- AI-suggested deletions (old promotions, expired content)

**B. Client-Side Storage**
- Store recent emails locally
- P2P backup network for redundancy
- Privacy-preserving encryption

### Recommended Implementation Plan

#### Phase 1: Quick Wins (Month 1-2)
1. **Attachment deduplication** within user
   - 20% storage savings
   - Low risk, high impact

2. **Basic compression** for old emails
   - 15% additional savings
   - Transparent to users

#### Phase 2: Medium Term (Month 3-6)
1. **Cross-user deduplication** for newsletters
   - 10% savings
   - Requires privacy framework

2. **Hierarchical storage** implementation
   - 40% cost reduction
   - Minor UX impact

#### Phase 3: Long Term (Month 6-12)
1. **ML-based archival** predictions
   - 5% additional optimization
   - Improved user experience

2. **Client-side hybrid** storage
   - 10% server storage reduction
   - Faster access for users

### Technical Architecture

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Ingestion │────▶│ Deduplication│────▶│ Compression │
└─────────────┘     └──────────────┘     └─────────────┘
                            │
                    ┌───────▼────────┐
                    │ Storage Manager │
                    └───────┬────────┘
        ┌───────────────────┼───────────────────┐
        ▼                   ▼                   ▼
   ┌─────────┐       ┌─────────┐         ┌─────────┐
   │   Hot   │       │  Warm   │         │  Cold   │
   │  (SSD)  │       │  (HDD)  │         │ (Tape)  │
   └─────────┘       └─────────┘         └─────────┘
```

### Expected Outcomes

**Storage Reduction**: 50-60% total
**Cost Savings**: $100M+ annually
**Performance**: 10% faster for recent emails
**User Impact**: Minimal (< 1% complaints)

### Risk Mitigation

1. **Data Loss**: 3x redundancy maintained
2. **Privacy**: Zero-knowledge deduplication
3. **Performance**: Caching layer for cold storage
4. **User Backlash**: Gradual rollout with opt-out

---

# Question 5: Design a Blogging Application

## Question
"How would you design a blogging application?"

### Modern Full-Stack Approach

#### 1. Requirements Gathering (2 minutes)

**Functional Requirements:**
- Create, edit, delete posts
- Comments and reactions
- User authentication
- Categories/tags
- Search functionality
- Media uploads

**Non-Functional Requirements:**
- Scale: 10M monthly active users
- Performance: < 2s page load
- Availability: 99.9% uptime
- SEO-friendly

#### 2. System Architecture

```
┌────────────────────────────────────────────────────┐
│                   Load Balancer                     │
└────────────────────┬──────────────┬────────────────┘
                     │              │
         ┌───────────▼───┐  ┌───────▼────────┐
         │   Web Server  │  │   Web Server   │
         │   (Next.js)   │  │   (Next.js)    │
         └───────┬───────┘  └────────┬───────┘
                 │                    │
         ┌───────▼────────────────────▼───────┐
         │          API Gateway               │
         │        (Authentication)            │
         └────┬─────────┬─────────┬──────────┘
              │         │         │
    ┌─────────▼──┐  ┌──▼─────┐ ┌─▼────────┐
    │   Posts    │  │ Users  │ │Comments  │
    │  Service   │  │Service │ │ Service  │
    └─────┬──────┘  └────┬───┘ └────┬─────┘
          │              │           │
    ┌─────▼──────────────▼───────────▼─────┐
    │          PostgreSQL                   │
    │    (Primary Database Cluster)         │
    └───────────────┬───────────────────────┘
                    │
    ┌───────────────▼───────────────────────┐
    │        Redis (Caching)                │
    └───────────────────────────────────────┘
    
    ┌───────────────────────────────────────┐
    │     CDN (Images, Static Assets)       │
    └───────────────────────────────────────┘
```

#### 3. Data Models

**Users Table:**
```sql
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    email VARCHAR(255) UNIQUE NOT NULL,
    username VARCHAR(50) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    bio TEXT,
    avatar_url VARCHAR(500),
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_username ON users(username);
```

**Posts Table:**
```sql
CREATE TABLE posts (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    author_id UUID REFERENCES users(id),
    title VARCHAR(255) NOT NULL,
    slug VARCHAR(255) UNIQUE NOT NULL,
    content TEXT NOT NULL,
    excerpt TEXT,
    featured_image VARCHAR(500),
    status VARCHAR(20) DEFAULT 'draft',
    view_count INTEGER DEFAULT 0,
    published_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_posts_author ON posts(author_id);
CREATE INDEX idx_posts_slug ON posts(slug);
CREATE INDEX idx_posts_published ON posts(published_at DESC);
```

**Comments Table:**
```sql
CREATE TABLE comments (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    post_id UUID REFERENCES posts(id) ON DELETE CASCADE,
    user_id UUID REFERENCES users(id),
    parent_id UUID REFERENCES comments(id),
    content TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_comments_post ON comments(post_id);
CREATE INDEX idx_comments_parent ON comments(parent_id);
```

**Tags & Categories:**
```sql
CREATE TABLE tags (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    name VARCHAR(50) UNIQUE NOT NULL,
    slug VARCHAR(50) UNIQUE NOT NULL
);

CREATE TABLE post_tags (
    post_id UUID REFERENCES posts(id) ON DELETE CASCADE,
    tag_id UUID REFERENCES tags(id) ON DELETE CASCADE,
    PRIMARY KEY (post_id, tag_id)
);
```

#### 4. API Design (RESTful)

**Authentication:**
```
POST   /api/auth/register
POST   /api/auth/login
POST   /api/auth/logout
GET    /api/auth/me
```

**Posts:**
```
GET    /api/posts           # List posts (paginated)
GET    /api/posts/:slug     # Get single post
POST   /api/posts           # Create post
PUT    /api/posts/:id       # Update post
DELETE /api/posts/:id       # Delete post
```

**Comments:**
```
GET    /api/posts/:id/comments    # Get comments
POST   /api/posts/:id/comments    # Add comment
DELETE /api/comments/:id          # Delete comment
```

**Search:**
```
GET    /api/search?q=term         # Full-text search
```

#### 5. Key Features Implementation

**A. Rich Text Editor**
```javascript
// Using TipTap or Quill.js
const editor = new Editor({
  extensions: [
    StarterKit,
    Image,
    Link,
    CodeBlock,
    Table
  ],
  content: post.content,
  onUpdate: ({ editor }) => {
    updatePost(editor.getHTML())
  }
})
```

**B. Real-time Comments**
```javascript
// WebSocket connection for live comments
const ws = new WebSocket('wss://api.blog.com/comments');

ws.on('comment:new', (comment) => {
  addCommentToUI(comment);
});

ws.on('comment:deleted', (commentId) => {
  removeCommentFromUI(commentId);
});
```

**C. SEO Optimization**
```javascript
// Server-side rendering with Next.js
export async function getServerSideProps({ params }) {
  const post = await fetchPost(params.slug);
  
  return {
    props: {
      post,
      meta: {
        title: post.title,
        description: post.excerpt,
        image: post.featured_image,
        url: `https://blog.com/posts/${post.slug}`
      }
    }
  };
}
```

**D. Caching Strategy**
```python
# Redis caching decorator
@cache(ttl=3600)
def get_popular_posts():
    return Post.objects.filter(
        status='published'
    ).order_by('-view_count')[:10]

# Cache invalidation
def update_post(post_id, data):
    post = Post.objects.update(post_id, data)
    cache.delete(f'post:{post_id}')
    cache.delete('popular_posts')
    return post
```

#### 6. Performance Optimizations

**Database:**
- Read replicas for scaling
- Query optimization with EXPLAIN
- Connection pooling

**Caching:**
- Redis for hot data
- CDN for static assets
- Browser caching headers

**Frontend:**
- Lazy loading images
- Code splitting
- Progressive Web App

#### 7. Monitoring & Analytics

```javascript
// Track key metrics
analytics.track('post_viewed', {
  post_id: post.id,
  user_id: user?.id,
  referrer: document.referrer
});

// Performance monitoring
const perfData = window.performance.timing;
const pageLoadTime = perfData.loadEventEnd - perfData.navigationStart;
monitoring.record('page_load_time', pageLoadTime);
```

### Scaling Considerations

1. **Database Sharding**: Shard by user_id
2. **Microservices**: Split into posts, users, comments services
3. **Message Queue**: For async tasks (email, notifications)
4. **ElasticSearch**: For advanced search functionality

---

# Question 6: Detect Duplicate Websites

## Question
"You're part of the Google Search web spam team. How would you detect duplicate websites?"

### Problem Understanding

**Why This Matters:**
- SEO manipulation (content farms)
- Copyright infringement
- Poor user experience
- Wasted crawl budget

**Types of Duplicates:**
1. Exact copies
2. Near duplicates (minor changes)
3. Translated copies
4. Templated content

### Multi-Layered Detection Approach

#### Layer 1: Content Fingerprinting

**A. SimHash Algorithm**
```python
def simhash(text):
    # 1. Tokenize and hash
    tokens = tokenize(text)
    hash_values = [hash(token) for token in tokens]
    
    # 2. Weight by frequency
    weighted_hashes = []
    for token in tokens:
        weight = tf_idf(token)
        hash_val = hash(token)
        weighted_hashes.append((hash_val, weight))
    
    # 3. Sum bit vectors
    bit_sum = [0] * 64
    for hash_val, weight in weighted_hashes:
        for i in range(64):
            if hash_val & (1 << i):
                bit_sum[i] += weight
            else:
                bit_sum[i] -= weight
    
    # 4. Generate fingerprint
    fingerprint = 0
    for i in range(64):
        if bit_sum[i] > 0:
            fingerprint |= (1 << i)
    
    return fingerprint

# Hamming distance for similarity
def similarity(hash1, hash2):
    xor = hash1 ^ hash2
    distance = bin(xor).count('1')
    return 1 - (distance / 64.0)
```

**B. MinHash for Scalability**
```python
def minhash(document, num_hashes=128):
    shingles = generate_shingles(document, k=5)
    signature = []
    
    for i in range(num_hashes):
        min_hash = float('inf')
        for shingle in shingles:
            hash_val = hash(shingle + str(i))
            min_hash = min(min_hash, hash_val)
        signature.append(min_hash)
    
    return signature

# LSH for efficient similarity search
def lsh_buckets(signature, bands=32, rows=4):
    buckets = []
    for i in range(bands):
        band = signature[i*rows:(i+1)*rows]
        bucket = hash(tuple(band))
        buckets.append(bucket)
    return buckets
```

#### Layer 2: Structural Analysis

**DOM Tree Similarity**
```python
def dom_similarity(dom1, dom2):
    # Extract structural features
    features1 = {
        'depth': max_depth(dom1),
        'tags': count_tags(dom1),
        'classes': extract_classes(dom1),
        'ids': extract_ids(dom1),
        'structure': tree_structure(dom1)
    }
    
    features2 = extract_features(dom2)
    
    # Calculate similarity scores
    scores = {
        'structure': tree_edit_distance(
            features1['structure'], 
            features2['structure']
        ),
        'css': jaccard_similarity(
            features1['classes'], 
            features2['classes']
        ),
        'layout': compare_layouts(dom1, dom2)
    }
    
    return weighted_average(scores)
```

#### Layer 3: Behavioral Signals

**JavaScript Execution Patterns**
```python
def detect_template_behavior():
    signals = {
        'loading_pattern': analyze_resource_loading(),
        'api_calls': track_external_apis(),
        'dom_mutations': monitor_dom_changes(),
        'event_handlers': fingerprint_js_behavior()
    }
    
    return generate_behavior_signature(signals)
```

#### Layer 4: Link Analysis

**Link Graph Patterns**
```python
def analyze_link_patterns(site1, site2):
    # Outbound links
    outbound1 = extract_external_links(site1)
    outbound2 = extract_external_links(site2)
    
    # Inbound links (from index)
    inbound1 = get_backlinks(site1)
    inbound2 = get_backlinks(site2)
    
    # Calculate similarities
    metrics = {
        'outbound_overlap': jaccard(outbound1, outbound2),
        'inbound_overlap': jaccard(inbound1, inbound2),
        'anchor_text_similarity': compare_anchor_texts(),
        'link_velocity': compare_link_growth_rates()
    }
    
    return metrics
```

#### Layer 5: Machine Learning Ensemble

**Feature Engineering**
```python
def extract_features(url):
    features = {
        # Content features
        'content_simhash': simhash(get_content(url)),
        'content_length': len(get_content(url)),
        'unique_words': count_unique_words(url),
        
        # Structural features
        'dom_depth': get_dom_depth(url),
        'css_rules': count_css_rules(url),
        'js_files': count_js_files(url),
        
        # Behavioral features
        'load_time': measure_load_time(url),
        'resource_count': count_resources(url),
        
        # Historical features
        'first_seen': get_first_crawl_date(url),
        'update_frequency': calculate_update_freq(url),
        
        # Network features
        'ip_address': get_ip(url),
        'hosting_provider': get_hosting_info(url),
        'ssl_certificate': get_ssl_fingerprint(url)
    }
    
    return features

# Gradient Boosting Classifier
model = XGBClassifier(
    n_estimators=1000,
    max_depth=8,
    learning_rate=0.01
)

model.fit(X_train, y_train)
duplicate_probability = model.predict_proba(features)
```

### Implementation Strategy

#### Phase 1: Real-time Detection
```python
def crawl_time_detection(new_url):
    # Quick checks during crawl
    content = fetch_content(new_url)
    
    # 1. Exact hash check
    content_hash = md5(content)
    if content_hash in hash_database:
        return {'duplicate': True, 'original': hash_database[content_hash]}
    
    # 2. SimHash check
    sim_hash = simhash(content)
    candidates = find_similar_simhashes(sim_hash, threshold=0.95)
    
    if candidates:
        return {'duplicate': True, 'similar_to': candidates}
    
    # Store for future comparison
    store_fingerprints(new_url, content_hash, sim_hash)
    return {'duplicate': False}
```

#### Phase 2: Batch Processing
```python
def batch_duplicate_detection():
    # Run daily on entire index
    
    # 1. Generate signatures for all pages
    signatures = spark.parallelize(all_urls) \
        .map(lambda url: (url, generate_signature(url))) \
        .cache()
    
    # 2. Find similar pairs using LSH
    similar_pairs = signatures \
        .flatMap(lambda x: lsh_emit_candidates(x)) \
        .groupByKey() \
        .filter(lambda x: len(x[1]) > 1) \
        .map(lambda x: verify_similarity(x[1]))
    
    # 3. Cluster duplicates
    duplicate_clusters = build_clusters(similar_pairs)
    
    # 4. Determine canonical URL for each cluster
    canonical_urls = duplicate_clusters \
        .map(lambda cluster: select_canonical(cluster))
    
    return canonical_urls
```

### Handling Edge Cases

1. **Legitimate Duplicates**
   - Mirror sites (different regions)
   - Mobile/desktop versions
   - HTTP/HTTPS versions
   
   Solution: Canonical URL detection

2. **Dynamic Content**
   - News sites with changing content
   - E-commerce with rotating products
   
   Solution: Template extraction, core content identification

3. **Internationalization**
   - Same content in different languages
   
   Solution: Language-agnostic structural comparison

### Success Metrics

- **Precision**: % of detected duplicates that are actual duplicates
- **Recall**: % of actual duplicates that are detected  
- **Latency**: Time to detect duplicate during crawl
- **Scale**: Billions of URLs processed daily

---

# Question 7: Meeting Conflict Detection

## Question
"Write an algorithm that detects meeting conflicts."

### Problem Analysis

**Input**: List of meetings with start and end times
**Output**: List of conflicting meeting pairs
**Edge Cases**: 
- Meetings that touch but don't overlap
- All-day meetings
- Recurring meetings

### Progressive Solutions

#### Solution 1: Basic O(n²) Approach
```python
def detect_conflicts_naive(meetings):
    """
    Simple approach - compare every pair
    Time: O(n²), Space: O(1)
    """
    conflicts = []
    
    for i in range(len(meetings)):
        for j in range(i + 1, len(meetings)):
            if meetings_overlap(meetings[i], meetings[j]):
                conflicts.append((i, j))
    
    return conflicts

def meetings_overlap(m1, m2):
    """Check if two meetings overlap"""
    # Meetings overlap if one starts before the other ends
    return m1['start'] < m2['end'] and m2['start'] < m1['end']
```

#### Solution 2: Optimized O(n log n) Approach
```python
def detect_conflicts_optimized(meetings):
    """
    Sort first, then sweep
    Time: O(n log n), Space: O(n)
    """
    # Create events for start and end times
    events = []
    for i, meeting in enumerate(meetings):
        events.append((meeting['start'], 'start', i))
        events.append((meeting['end'], 'end', i))
    
    # Sort events by time, with 'end' before 'start' for same time
    events.sort(key=lambda x: (x[0], x[1] == 'start'))
    
    active_meetings = set()
    conflicts = []
    
    for time, event_type, meeting_id in events:
        if event_type == 'start':
            # Check conflicts with all active meetings
            for active_id in active_meetings:
                conflicts.append((active_id, meeting_id))
            active_meetings.add(meeting_id)
        else:
            active_meetings.remove(meeting_id)
    
    return conflicts
```

#### Solution 3: Interval Tree for Dynamic Updates
```python
class IntervalNode:
    def __init__(self, start, end, meeting_id):
        self.start = start
        self.end = end
        self.meeting_id = meeting_id
        self.max_end = end
        self.left = None
        self.right = None

class IntervalTree:
    def __init__(self):
        self.root = None
    
    def insert(self, start, end, meeting_id):
        """Insert a meeting and return conflicts"""
        conflicts = []
        self._find_conflicts(self.root, start, end, conflicts)
        self.root = self._insert(self.root, start, end, meeting_id)
        return conflicts
    
    def _insert(self, node, start, end, meeting_id):
        if not node:
            return IntervalNode(start, end, meeting_id)
        
        if start < node.start:
            node.left = self._insert(node.left, start, end, meeting_id)
        else:
            node.right = self._insert(node.right, start, end, meeting_id)
        
        node.max_end = max(node.max_end, end)
        return node
    
    def _find_conflicts(self, node, start, end, conflicts):
        if not node:
            return
        
        # Check if current node conflicts
        if node.start < end and start < node.end:
            conflicts.append(node.meeting_id)
        
        # Explore left subtree if possible conflicts
        if node.left and node.left.max_end > start:
            self._find_conflicts(node.left, start, end, conflicts)
        
        # Explore right subtree if possible conflicts  
        if node.right and node.start < end:
            self._find_conflicts(node.right, start, end, conflicts)
```

#### Solution 4: Real-World Implementation
```python
from datetime import datetime, timedelta
from collections import defaultdict
import heapq

class MeetingScheduler:
    def __init__(self):
        self.meetings = []
        self.user_calendars = defaultdict(list)
        
    def add_meeting(self, meeting):
        """
        Add meeting and check conflicts
        
        meeting = {
            'id': 'unique_id',
            'title': 'Team Standup',
            'start': datetime,
            'end': datetime,
            'attendees': ['user1', 'user2'],
            'room': 'Conference Room A',
            'recurring': {
                'frequency': 'daily|weekly|monthly',
                'until': datetime,
                'exceptions': [datetime, ...]
            }
        }
        """
        conflicts = self.find_conflicts(meeting)
        
        if not conflicts:
            self.meetings.append(meeting)
            for attendee in meeting['attendees']:
                self.user_calendars[attendee].append(meeting)
        
        return conflicts
    
    def find_conflicts(self, new_meeting):
        conflicts = {
            'time_conflicts': [],
            'room_conflicts': [],
            'attendee_conflicts': defaultdict(list)
        }
        
        # Expand recurring meetings
        meeting_instances = self._expand_recurring(new_meeting)
        
        for instance in meeting_instances:
            for existing in self.meetings:
                existing_instances = self._expand_recurring(existing)
                
                for exist_instance in existing_instances:
                    if self._overlaps(instance, exist_instance):
                        # Time conflict
                        conflicts['time_conflicts'].append({
                            'meeting': existing,
                            'conflicting_time': (instance['start'], instance['end'])
                        })
                        
                        # Room conflict
                        if (instance.get('room') and 
                            instance['room'] == exist_instance.get('room')):
                            conflicts['room_conflicts'].append({
                                'room': instance['room'],
                                'conflicting_meeting': existing,
                                'time': (instance['start'], instance['end'])
                            })
                        
                        # Attendee conflicts
                        common_attendees = set(instance['attendees']) & \
                                         set(exist_instance['attendees'])
                        for attendee in common_attendees:
                            conflicts['attendee_conflicts'][attendee].append({
                                'conflicting_meeting': existing,
                                'time': (instance['start'], instance['end'])
                            })
        
        return conflicts if any(conflicts.values()) else None
    
    def _expand_recurring(self, meeting, limit=365):
        """Expand recurring meetings into individual instances"""
        if 'recurring' not in meeting:
            return [meeting]
        
        instances = []
        current = meeting['start']
        recurring = meeting['recurring']
        
        while current <= recurring.get('until', meeting['start'] + timedelta(days=limit)):
            if current not in recurring.get('exceptions', []):
                instance = meeting.copy()
                instance['start'] = current
                instance['end'] = current + (meeting['end'] - meeting['start'])
                instances.append(instance)
            
            # Next occurrence
            if recurring['frequency'] == 'daily':
                current += timedelta(days=1)
            elif recurring['frequency'] == 'weekly':
                current += timedelta(weeks=1)
            elif recurring['frequency'] == 'monthly':
                # Handle month boundaries properly
                if current.month == 12:
                    current = current.replace(year=current.year + 1, month=1)
                else:
                    current = current.replace(month=current.month + 1)
        
        return instances
    
    def _overlaps(self, m1, m2):
        """Check if two meeting instances overlap"""
        return m1['start'] < m2['end'] and m2['start'] < m1['end']
    
    def suggest_alternatives(self, meeting, constraints=None):
        """Suggest alternative meeting times"""
        suggestions = []
        duration = meeting['end'] - meeting['start']
        
        # Try slots in the next 7 days
        current_slot = meeting['start']
        attempts = 0
        
        while len(suggestions) < 3 and attempts < 100:
            attempts += 1
            
            # Check if slot is free for all attendees
            test_meeting = meeting.copy()
            test_meeting['start'] = current_slot
            test_meeting['end'] = current_slot + duration
            
            conflicts = self.find_conflicts(test_meeting)
            
            if not conflicts:
                suggestions.append({
                    'start': current_slot,
                    'end': current_slot + duration,
                    'score': self._score_slot(current_slot, constraints)
                })
            
            # Try next slot
            current_slot += timedelta(minutes=30)
            
            # Skip weekends and non-business hours
            if current_slot.weekday() >= 5:  # Weekend
                current_slot += timedelta(days=2)
            elif current_slot.hour >= 18:  # After 6 PM
                current_slot = current_slot.replace(
                    hour=9, minute=0
                ) + timedelta(days=1)
        
        # Sort by score
        suggestions.sort(key=lambda x: x['score'], reverse=True)
        return suggestions
    
    def _score_slot(self, slot, constraints):
        """Score a time slot based on preferences"""
        score = 100
        
        # Prefer mid-morning and mid-afternoon
        if 10 <= slot.hour <= 11 or 14 <= slot.hour <= 15:
            score += 20
        
        # Penalize early morning and late afternoon
        if slot.hour < 9 or slot.hour > 17:
            score -= 30
        
        # Penalize Monday morning and Friday afternoon
        if slot.weekday() == 0 and slot.hour < 12:
            score -= 10
        elif slot.weekday() == 4 and slot.hour > 15:
            score -= 10
        
        return score
```

### Testing Strategy

```python
def test_meeting_conflicts():
    scheduler = MeetingScheduler()
    
    # Test case 1: Simple overlap
    m1 = {
        'id': '1',
        'start': datetime(2024, 1, 15, 10, 0),
        'end': datetime(2024, 1, 15, 11, 0),
        'attendees': ['alice', 'bob'],
        'room': 'Room A'
    }
    
    m2 = {
        'id': '2', 
        'start': datetime(2024, 1, 15, 10, 30),
        'end': datetime(2024, 1, 15, 11, 30),
        'attendees': ['alice', 'charlie'],
        'room': 'Room A'
    }
    
    scheduler.add_meeting(m1)
    conflicts = scheduler.add_meeting(m2)
    
    assert conflicts is not None
    assert len(conflicts['time_conflicts']) == 1
    assert len(conflicts['room_conflicts']) == 1
    assert 'alice' in conflicts['attendee_conflicts']
    
    # Test case 2: Recurring meetings
    m3 = {
        'id': '3',
        'start': datetime(2024, 1, 15, 14, 0),
        'end': datetime(2024, 1, 15, 15, 0),
        'attendees': ['alice'],
        'recurring': {
            'frequency': 'weekly',
            'until': datetime(2024, 2, 15)
        }
    }
    
    # This should conflict with the weekly recurring meeting
    m4 = {
        'id': '4',
        'start': datetime(2024, 1, 22, 14, 30),
        'end': datetime(2024, 1, 22, 15, 30),
        'attendees': ['alice']
    }
    
    scheduler.add_meeting(m3)
    conflicts = scheduler.add_meeting(m4)
    
    assert conflicts is not None
    
    print("All tests passed!")
```

---

# Question 8: Elevator Control System

## Question
"Design an elevator control system."

### System Requirements

**Functional:**
- Handle multiple elevator cars
- Optimize for minimum wait time
- Support different operation modes
- Handle emergencies

**Non-Functional:**
- Real-time response (<100ms)
- High reliability (99.99% uptime)
- Scalable to 100+ floors
- Energy efficient

### System Architecture

```python
from enum import Enum
from heapq import heappush, heappop
from collections import deque
import time
import threading

class Direction(Enum):
    UP = 1
    DOWN = -1
    IDLE = 0

class RequestType(Enum):
    INTERNAL = "internal"  # From inside elevator
    EXTERNAL = "external"  # From floor

class ElevatorState(Enum):
    IDLE = "idle"
    MOVING = "moving"
    DOORS_OPEN = "doors_open"
    MAINTENANCE = "maintenance"
    EMERGENCY = "emergency"

class Request:
    def __init__(self, floor, direction=None, request_type=RequestType.EXTERNAL):
        self.floor = floor
        self.direction = direction
        self.request_type = request_type
        self.timestamp = time.time()

class Elevator:
    def __init__(self, id, capacity=10, floors=20):
        self.id = id
        self.current_floor = 1
        self.direction = Direction.IDLE
        self.state = ElevatorState.IDLE
        self.capacity = capacity
        self.current_load = 0
        self.destination_queue = []
        self.floors = floors
        self.speed = 2.0  # seconds per floor
        self.door_time = 3.0  # seconds for doors
        
    def calculate_cost(self, request):
        """Calculate cost to serve a request"""
        distance = abs(self.current_floor - request.floor)
        
        # Base cost is distance
        cost = distance
        
        # Penalty for changing direction
        if self.direction != Direction.IDLE:
            if self.direction == Direction.UP and request.floor < self.current_floor:
                cost += self.floors
            elif self.direction == Direction.DOWN and request.floor > self.current_floor:
                cost += self.floors
        
        # Penalty for capacity
        if self.current_load >= self.capacity * 0.8:
            cost += 10
            
        return cost
```

### Scheduling Algorithms

#### 1. FCFS (First Come First Served)
```python
class FCFSScheduler:
    def __init__(self, elevators):
        self.elevators = elevators
        self.request_queue = deque()
    
    def add_request(self, request):
        self.request_queue.append(request)
        self.dispatch()
    
    def dispatch(self):
        while self.request_queue:
            request = self.request_queue.popleft()
            
            # Find first available elevator
            for elevator in self.elevators:
                if elevator.state == ElevatorState.IDLE:
                    elevator.add_destination(request.floor)
                    break
```

#### 2. SCAN (Elevator Algorithm)
```python
class SCANScheduler:
    def __init__(self, elevators):
        self.elevators = elevators
        self.up_requests = []
        self.down_requests = []
    
    def add_request(self, request):
        if request.direction == Direction.UP:
            heappush(self.up_requests, request.floor)
        else:
            heappush(self.down_requests, -request.floor)
        
        self.dispatch()
    
    def dispatch(self):
        for elevator in self.elevators:
            if elevator.state != ElevatorState.IDLE:
                continue
                
            if elevator.direction == Direction.UP:
                # Serve all up requests above current floor
                while self.up_requests and self.up_requests[0] >= elevator.current_floor:
                    floor = heappop(self.up_requests)
                    elevator.add_destination(floor)
                
                # Change direction if no more up requests
                if not elevator.destination_queue:
                    elevator.direction = Direction.DOWN
                    
            elif elevator.direction == Direction.DOWN:
                # Serve all down requests below current floor
                while self.down_requests and -self.down_requests[0] <= elevator.current_floor:
                    floor = -heappop(self.down_requests)
                    elevator.add_destination(floor)
                
                # Change direction if no more down requests
                if not elevator.destination_queue:
                    elevator.direction = Direction.UP
```

#### 3. Advanced: Minimum Cost Algorithm
```python
class OptimalScheduler:
    def __init__(self, elevators):
        self.elevators = elevators
        self.pending_requests = []
        
    def add_request(self, request):
        self.pending_requests.append(request)
        self.optimize_and_dispatch()
    
    def optimize_and_dispatch(self):
        """Use dynamic programming to minimize total wait time"""
        if not self.pending_requests:
            return
            
        # Calculate cost matrix
        n_requests = len(self.pending_requests)
        n_elevators = len(self.elevators)
        cost_matrix = [[float('inf')] * n_requests for _ in range(n_elevators)]
        
        for i, elevator in enumerate(self.elevators):
            for j, request in enumerate(self.pending_requests):
                if elevator.state == ElevatorState.IDLE or elevator.state == ElevatorState.MOVING:
                    cost_matrix[i][j] = elevator.calculate_cost(request)
        
        # Assign requests to minimize total cost
        assignments = self.hungarian_algorithm(cost_matrix)
        
        # Dispatch based on assignments
        for elevator_idx, request_idx in assignments:
            if request_idx < len(self.pending_requests):
                elevator = self.elevators[elevator_idx]
                request = self.pending_requests[request_idx]
                elevator.add_destination(request.floor)
        
        # Clear assigned requests
        self.pending_requests = []
    
    def hungarian_algorithm(self, cost_matrix):
        """Simplified Hungarian algorithm for assignment"""
        # This is a placeholder - real implementation would be more complex
        assignments = []
        used_requests = set()
        
        for i, elevator_costs in enumerate(cost_matrix):
            min_cost = float('inf')
            min_idx = -1
            
            for j, cost in enumerate(elevator_costs):
                if j not in used_requests and cost < min_cost:
                    min_cost = cost
                    min_idx = j
            
            if min_idx != -1:
                assignments.append((i, min_idx))
                used_requests.add(min_idx)
        
        return assignments
```

### Complete System Implementation

```python
class ElevatorControlSystem:
    def __init__(self, num_elevators=4, num_floors=20, algorithm='optimal'):
        self.num_elevators = num_elevators
        self.num_floors = num_floors
        self.elevators = [Elevator(i, floors=num_floors) for i in range(num_elevators)]
        
        # Choose scheduling algorithm
        algorithms = {
            'fcfs': FCFSScheduler,
            'scan': SCANScheduler,
            'optimal': OptimalScheduler
        }
        self.scheduler = algorithms[algorithm](self.elevators)
        
        # Monitoring
        self.total_wait_time = 0
        self.total_requests = 0
        self.request_log = []
        
        # Start elevator threads
        for elevator in self.elevators:
            thread = threading.Thread(target=self.elevator_controller, args=(elevator,))
            thread.daemon = True
            thread.start()
    
    def elevator_controller(self, elevator):
        """Control loop for individual elevator"""
        while True:
            if elevator.destination_queue:
                next_floor = elevator.destination_queue[0]
                
                # Move towards destination
                if next_floor > elevator.current_floor:
                    elevator.direction = Direction.UP
                    elevator.state = ElevatorState.MOVING
                    time.sleep(elevator.speed)  # Simulate movement
                    elevator.current_floor += 1
                elif next_floor < elevator.current_floor:
                    elevator.direction = Direction.DOWN
                    elevator.state = ElevatorState.MOVING
                    time.sleep(elevator.speed)  # Simulate movement
                    elevator.current_floor -= 1
                else:
                    # Arrived at destination
                    elevator.destination_queue.pop(0)
                    elevator.state = ElevatorState.DOORS_OPEN
                    time.sleep(elevator.door_time)  # Simulate door operation
                    
                    # Update load (simplified)
                    elevator.current_load = max(0, elevator.current_load + 
                                              random.randint(-3, 3))
                    
                    if not elevator.destination_queue:
                        elevator.state = ElevatorState.IDLE
                        elevator.direction = Direction.IDLE
            else:
                elevator.state = ElevatorState.IDLE
                elevator.direction = Direction.IDLE
                time.sleep(0.1)  # Idle polling
    
    def request_elevator(self, floor, direction=None):
        """Public API for requesting an elevator"""
        if floor < 1 or floor > self.num_floors:
            raise ValueError(f"Invalid floor: {floor}")
        
        request = Request(floor, direction, RequestType.EXTERNAL)
        self.scheduler.add_request(request)
        
        # Log for analytics
        self.request_log.append({
            'timestamp': request.timestamp,
            'floor': floor,
            'direction': direction
        })
        
        return self.estimate_arrival_time(floor)
    
    def estimate_arrival_time(self, floor):
        """Estimate arrival time for a floor request"""
        min_time = float('inf')
        
        for elevator in self.elevators:
            # Simple estimation
            distance = abs(elevator.current_floor - floor)
            queue_length = len(elevator.destination_queue)
            
            estimated_time = (distance * elevator.speed + 
                            queue_length * (elevator.speed + elevator.door_time))
            
            min_time = min(min_time, estimated_time)
        
        return min_time
    
    def emergency_stop(self, elevator_id):
        """Emergency stop for specific elevator"""
        if 0 <= elevator_id < self.num_elevators:
            elevator = self.elevators[elevator_id]
            elevator.state = ElevatorState.EMERGENCY
            elevator.destination_queue.clear()
            # Alert building management
            self.alert_emergency(elevator_id, elevator.current_floor)
    
    def get_system_status(self):
        """Get current system status for monitoring"""
        status = {
            'elevators': [],
            'avg_wait_time': self.total_wait_time / max(1, self.total_requests),
            'total_requests': self.total_requests
        }
        
        for elevator in self.elevators:
            status['elevators'].append({
                'id': elevator.id,
                'floor': elevator.current_floor,
                'direction': elevator.direction.name,
                'state': elevator.state.name,
                'load': f"{elevator.current_load}/{elevator.capacity}",
                'queue_length': len(elevator.destination_queue)
            })
        
        return status
```

### Advanced Features

#### 1. Predictive Scheduling
```python
class PredictiveScheduler(OptimalScheduler):
    def __init__(self, elevators):
        super().__init__(elevators)
        self.traffic_patterns = self.load_traffic_patterns()
    
    def load_traffic_patterns(self):
        """Load historical traffic patterns"""
        return {
            'morning_rush': {
                'time': (7, 9),
                'pattern': 'up_heavy',
                'floors': [1]  # Most traffic from ground floor
            },
            'lunch': {
                'time': (12, 13),
                'pattern': 'bidirectional',
                'floors': [1, 10, 15]  # Cafeteria floors
            },
            'evening_rush': {
                'time': (17, 19),
                'pattern': 'down_heavy',
                'floors': list(range(2, 20))  # All office floors
            }
        }
    
    def predict_next_requests(self):
        """Predict likely next requests based on patterns"""
        current_hour = time.localtime().tm_hour
        predictions = []
        
        for pattern_name, pattern in self.traffic_patterns.items():
            start_hour, end_hour = pattern['time']
            if start_hour <= current_hour < end_hour:
                for floor in pattern['floors']:
                    if pattern['pattern'] == 'up_heavy':
                        predictions.append(Request(floor, Direction.UP))
                    elif pattern['pattern'] == 'down_heavy':
                        predictions.append(Request(floor, Direction.DOWN))
        
        return predictions
    
    def position_elevators(self):
        """Pre-position elevators based on predictions"""
        predictions = self.predict_next_requests()
        
        if predictions:
            # Distribute idle elevators to predicted high-traffic floors
            idle_elevators = [e for e in self.elevators 
                            if e.state == ElevatorState.IDLE]
            
            for i, elevator in enumerate(idle_elevators):
                if i < len(predictions):
                    elevator.add_destination(predictions[i].floor)
```

#### 2. Energy Optimization
```python
class EnergyEfficientScheduler(OptimalScheduler):
    def calculate_energy_cost(self, elevator, request):
        """Calculate energy cost for serving request"""
        base_cost = elevator.calculate_cost(request)
        
        # Energy factors
        load_factor = elevator.current_load / elevator.capacity
        distance = abs(elevator.current_floor - request.floor)
        
        # Heavier loads use more energy
        energy_cost = distance * (1 + load_factor * 0.5)
        
        # Penalty for starting from idle (overcome inertia)
        if elevator.state == ElevatorState.IDLE:
            energy_cost += 2
        
        return base_cost + energy_cost * 0.3  # Weight energy vs time
    
    def group_requests(self, requests):
        """Group nearby requests to save energy"""
        groups = []
        sorted_requests = sorted(requests, key=lambda r: r.floor)
        
        current_group = []
        for request in sorted_requests:
            if not current_group:
                current_group.append(request)
            elif abs(request.floor - current_group[-1].floor) <= 2:
                current_group.append(request)
            else:
                groups.append(current_group)
                current_group = [request]
        
        if current_group:
            groups.append(current_group)
        
        return groups
```

### Testing and Simulation

```python
def simulate_building_traffic():
    """Simulate a day of building traffic"""
    system = ElevatorControlSystem(num_elevators=4, num_floors=20, algorithm='optimal')
    
    # Morning rush (7-9 AM)
    print("Simulating morning rush...")
    for _ in range(100):
        floor = random.choices([1], weights=[1])[0]  # Most from ground floor
        destination = random.randint(2, 20)
        system.request_elevator(floor, Direction.UP)
        time.sleep(random.uniform(0.5, 2))
    
    # Midday traffic (9 AM - 5 PM)
    print("Simulating midday traffic...")
    for _ in range(200):
        floor = random.randint(1, 20)
        direction = random.choice([Direction.UP, Direction.DOWN])
        system.request_elevator(floor, direction)
        time.sleep(random.uniform(2, 5))
    
    # Evening rush (5-7 PM)
    print("Simulating evening rush...")
    for _ in range(100):
        floor = random.randint(2, 20)
        system.request_elevator(floor, Direction.DOWN)
        time.sleep(random.uniform(0.5, 2))
    
    # Print statistics
    status = system.get_system_status()
    print(f"\nSimulation Complete:")
    print(f"Total Requests: {status['total_requests']}")
    print(f"Average Wait Time: {status['avg_wait_time']:.2f} seconds")
    print(f"Final Elevator Positions: {[e['floor'] for e in status['elevators']]}")
```

---

# Question 9: Server Bottleneck

## Question
"There's a server bottleneck. How would you solve it?"

### Systematic Diagnosis Approach

#### 1. Identify Bottleneck Type
```python
class BottleneckDiagnostics:
    def __init__(self):
        self.metrics = {
            'cpu_usage': self.check_cpu(),
            'memory_usage': self.check_memory(),
            'disk_io': self.check_disk(),
            'network_bandwidth': self.check_network(),
            'database_performance': self.check_database(),
            'application_profile': self.profile_application()
        }
    
    def diagnose(self):
        bottlenecks = []
        
        if self.metrics['cpu_usage'] > 80:
            bottlenecks.append({
                'type': 'CPU',
                'severity': 'high' if self.metrics['cpu_usage'] > 90 else 'medium',
                'details': f"CPU at {self.metrics['cpu_usage']}%"
            })
        
        if self.metrics['memory_usage'] > 85:
            bottlenecks.append({
                'type': 'Memory',
                'severity': 'high' if self.metrics['memory_usage'] > 95 else 'medium',
                'details': f"Memory at {self.metrics['memory_usage']}%"
            })
        
        # Similar checks for other metrics...
        
        return bottlenecks
```

### Solutions by Bottleneck Type

#### 1. CPU Bottleneck Solutions

**A. Code Optimization**
```python
# Before: Inefficient
def process_data_slow(items):
    result = []
    for item in items:
        if item > 0:
            for i in range(len(result)):
                if result[i] == item:
                    break
            else:
                result.append(item)
    return result

# After: Optimized
def process_data_fast(items):
    return list(set(item for item in items if item > 0))

# Even Better: NumPy for numerical operations
import numpy as np
def process_data_numpy(items):
    arr = np.array(items)
    return np.unique(arr[arr > 0])
```

**B. Parallel Processing**
```python
from multiprocessing import Pool
from concurrent.futures import ThreadPoolExecutor
import asyncio

class ParallelProcessor:
    @staticmethod
    def cpu_bound_parallel(data, num_processes=None):
        """For CPU-intensive tasks"""
        with Pool(processes=num_processes) as pool:
            results = pool.map(expensive_computation, data)
        return results
    
    @staticmethod
    def io_bound_parallel(urls):
        """For I/O-intensive tasks"""
        with ThreadPoolExecutor(max_workers=20) as executor:
            results = list(executor.map(fetch_url, urls))
        return results
    
    @staticmethod
    async def async_processing(tasks):
        """For async I/O operations"""
        results = await asyncio.gather(*tasks)
        return results
```

**C. Caching Strategy**
```python
from functools import lru_cache
import redis
import pickle

class CachingLayer:
    def __init__(self):
        self.redis_client = redis.Redis(host='localhost', port=6379)
        self.local_cache = {}
    
    # Memory caching for hot data
    @lru_cache(maxsize=1000)
    def get_user_data(self, user_id):
        return self.fetch_from_database(user_id)
    
    # Redis for distributed caching
    def get_cached_or_compute(self, key, compute_func, ttl=3600):
        # Try local cache first
        if key in self.local_cache:
            return self.local_cache[key]
        
        # Try Redis
        cached = self.redis_client.get(key)
        if cached:
            value = pickle.loads(cached)
            self.local_cache[key] = value
            return value
        
        # Compute and cache
        value = compute_func()
        
        # Store in Redis
        self.redis_client.setex(
            key, 
            ttl, 
            pickle.dumps(value)
        )
        
        # Store locally
        self.local_cache[key] = value
        
        return value
```

#### 2. Memory Bottleneck Solutions

**A. Memory Optimization**
```python
class MemoryOptimizer:
    @staticmethod
    def use_generators():
        """Use generators instead of lists for large datasets"""
        # Bad: Loads entire file into memory
        def read_file_bad(filename):
            with open(filename) as f:
                return f.readlines()
        
        # Good: Yields one line at a time
        def read_file_good(filename):
            with open(filename) as f:
                for line in f:
                    yield line.strip()
    
    @staticmethod
    def optimize_data_structures():
        """Use appropriate data structures"""
        # Use __slots__ to reduce memory overhead
        class OptimizedUser:
            __slots__ = ['id', 'name', 'email']
            
            def __init__(self, id, name, email):
                self.id = id
                self.name = name
                self.email = email
        
        # Use array.array for homogeneous data
        import array
        # Instead of: numbers = [1, 2, 3, 4, 5]
        numbers = array.array('i', [1, 2, 3, 4, 5])
```

**B. Memory Pooling**
```python
class ObjectPool:
    def __init__(self, create_func, reset_func, size=100):
        self.create_func = create_func
        self.reset_func = reset_func
        self.pool = [create_func() for _ in range(size)]
        self.available = set(self.pool)
    
    def acquire(self):
        if self.available:
            obj = self.available.pop()
            return obj
        return self.create_func()
    
    def release(self, obj):
        self.reset_func(obj)
        self.available.add(obj)

# Usage
def create_buffer():
    return bytearray(1024 * 1024)  # 1MB buffer

def reset_buffer(buf):
    buf[:] = b'\x00' * len(buf)

buffer_pool = ObjectPool(create_buffer, reset_buffer)
```

#### 3. Database Bottleneck Solutions

**A. Query Optimization**
```python
class DatabaseOptimizer:
    @staticmethod
    def optimize_queries():
        # Bad: N+1 query problem
        """
        users = User.objects.all()
        for user in users:
            print(user.orders.count())  # New query for each user
        """
        
        # Good: Use select_related/prefetch_related
        """
        users = User.objects.prefetch_related('orders').all()
        for user in users:
            print(user.orders.count())  # No additional queries
        """
        
        # Better: Aggregate in database
        """
        from django.db.models import Count
        users = User.objects.annotate(order_count=Count('orders'))
        for user in users:
            print(user.order_count)
        """
    
    @staticmethod
    def add_indexes():
        """Strategic index creation"""
        # Composite indexes for common queries
        """
        CREATE INDEX idx_user_status_created 
        ON users(status, created_at) 
        WHERE status = 'active';
        """
        
        # Covering indexes to avoid table lookups
        """
        CREATE INDEX idx_orders_covering 
        ON orders(user_id, created_at) 
        INCLUDE (total_amount, status);
        """
```

**B. Connection Pooling**
```python
from sqlalchemy import create_engine
from sqlalchemy.pool import QueuePool

class DatabaseConnectionPool:
    def __init__(self, database_url):
        self.engine = create_engine(
            database_url,
            poolclass=QueuePool,
            pool_size=20,
            max_overflow=40,
            pool_timeout=30,
            pool_pre_ping=True  # Verify connections before use
        )
    
    def execute_query(self, query):
        with self.engine.connect() as conn:
            result = conn.execute(query)
            return result.fetchall()
```

#### 4. Network Bottleneck Solutions

**A. CDN Implementation**
```python
class CDNStrategy:
    def __init__(self):
        self.cdn_endpoints = {
            'us-east': 'cdn-us-east.example.com',
            'us-west': 'cdn-us-west.example.com',
            'eu': 'cdn-eu.example.com',
            'asia': 'cdn-asia.example.com'
        }
    
    def get_optimal_cdn(self, user_location):
        """Route to nearest CDN endpoint"""
        # Simplified geo-routing logic
        if user_location.startswith('US'):
            return self.cdn_endpoints['us-east']
        elif user_location.startswith('EU'):
            return self.cdn_endpoints['eu']
        return self.cdn_endpoints['asia']
    
    def cache_headers(self, content_type):
        """Set appropriate cache headers"""
        cache_times = {
            'image': 86400 * 30,  # 30 days
            'css': 86400 * 7,     # 7 days
            'api': 300            # 5 minutes
        }
        
        return {
            'Cache-Control': f'public, max-age={cache_times.get(content_type, 3600)}',
            'Vary': 'Accept-Encoding',
            'ETag': self.generate_etag()
        }
```

**B. Request Batching**
```python
class RequestBatcher:
    def __init__(self, batch_size=100, max_wait_ms=50):
        self.batch_size = batch_size
        self.max_wait_ms = max_wait_ms
        self.pending_requests = []
        self.last_flush = time.time()
    
    async def add_request(self, request):
        self.pending_requests.append(request)
        
        if (len(self.pending_requests) >= self.batch_size or
            (time.time() - self.last_flush) * 1000 > self.max_wait_ms):
            await self.flush()
    
    async def flush(self):
        if not self.pending_requests:
            return
        
        batch = self.pending_requests[:self.batch_size]
        self.pending_requests = self.pending_requests[self.batch_size:]
        
        # Send batch request
        response = await self.send_batch(batch)
        self.last_flush = time.time()
        
        return response
```

### Comprehensive Solution Architecture

```python
class ScalableArchitecture:
    """Complete solution for handling server bottlenecks"""
    
    def __init__(self):
        # Load balancing
        self.load_balancer = self.setup_load_balancer()
        
        # Caching layers
        self.l1_cache = {}  # Application memory
        self.l2_cache = redis.Redis()  # Redis
        self.l3_cache = self.setup_cdn()  # CDN
        
        # Database optimization
        self.read_replicas = self.setup_read_replicas()
        self.write_master = self.setup_master_db()
        
        # Async processing
        self.message_queue = self.setup_queue()
        self.worker_pool = self.setup_workers()
    
    def handle_request(self, request):
        """Optimized request handling pipeline"""
        
        # 1. Check caches
        cached = self.check_caches(request.key)
        if cached:
            return cached
        
        # 2. Route read vs write
        if request.is_read:
            # Use read replica
            db = self.get_read_replica()
        else:
            # Use master + async processing
            db = self.write_master
            self.queue_async_tasks(request)
        
        # 3. Execute with timeout
        result = self.execute_with_timeout(db, request, timeout=5)
        
        # 4. Cache result
        self.update_caches(request.key, result)
        
        return result
    
    def auto_scale(self, metrics):
        """Auto-scaling based on metrics"""
        if metrics['cpu'] > 80 or metrics['response_time'] > 1000:
            self.scale_up()
        elif metrics['cpu'] < 20 and metrics['response_time'] < 100:
            self.scale_down()
    
    def scale_up(self):
        """Add more servers"""
        new_server = self.provision_server()
        self.load_balancer.add_server(new_server)
        
    def scale_down(self):
        """Remove underutilized servers"""
        least_loaded = self.load_balancer.get_least_loaded()
        self.load_balancer.remove_server(least_loaded)
        self.deprovision_server(least_loaded)
```

### Monitoring and Alerting

```python
class PerformanceMonitor:
    def __init__(self):
        self.metrics = defaultdict(list)
        self.alerts = []
    
    def track_metric(self, name, value):
        self.metrics[name].append({
            'value': value,
            'timestamp': time.time()
        })
        
        # Check thresholds
        self.check_alerts(name, value)
    
    def check_alerts(self, metric_name, value):
        thresholds = {
            'response_time': 1000,  # ms
            'error_rate': 0.01,     # 1%
            'cpu_usage': 80,        # %
            'memory_usage': 85      # %
        }
        
        if metric_name in thresholds and value > thresholds[metric_name]:
            self.trigger_alert(metric_name, value, thresholds[metric_name])
    
    def get_insights(self):
        """Analyze metrics for patterns"""
        insights = []
        
        for metric_name, values in self.metrics.items():
            recent = [v['value'] for v in values[-100:]]
            
            # Trend analysis
            if len(recent) > 10:
                trend = self.calculate_trend(recent)
                if trend > 0.1:  # 10% increase
                    insights.append({
                        'metric': metric_name,
                        'insight': 'increasing',
                        'trend': trend
                    })
            
            # Anomaly detection
            anomalies = self.detect_anomalies(recent)
            if anomalies:
                insights.append({
                    'metric': metric_name,
                    'insight': 'anomalies detected',
                    'anomalies': anomalies
                })
        
        return insights
```

### Best Practices Summary

1. **Identify First**: Use monitoring to identify the actual bottleneck
2. **Measure Impact**: Quantify the performance improvement needed
3. **Start Simple**: Try configuration changes before architecture changes
4. **Scale Horizontally**: Add more servers rather than bigger servers
5. **Cache Aggressively**: But invalidate intelligently
6. **Async Everything**: Don't block on I/O operations
7. **Monitor Continuously**: Set up alerts for proactive management
8. **Plan for Failure**: Design for graceful degradation

---

This completes the comprehensive technical questions guide. Each solution provides both theoretical understanding and practical implementation strategies suitable for PM interviews. 