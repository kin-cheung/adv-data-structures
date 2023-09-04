# System Design

## Requirements gathering
### 1. Functional requirements
 - Identify actors, user cases and user flows 
### 2. Non-functional requirements
 - measurable and testable
 - tradeoffs and feasibility
 - no one single architecture can serve all quality requirements
### 3. Limitations and boundaries
 - can make design simpler
 - technical (programming languages), business (budget), regulatory/legal constraints
   - be aware of self-imposed constraints that can be removed or avoided
 - Loosely couple current constraints or dependencies

## General considerations
 - performance - single host, multi-threaded, distributed, multi-region, edge computing, CDN, caching
 - availability - load balancing, replication, master/slave, election
 - consistency - sync/async
 - monitoring - core feature monitoring, algorithem efficiency

## Rate limiter
### Considerations
 - client side or server side
 - distributed or in-process
 - rules and cache them
 - soft limit and hard limit
 - return 429
### Algorithms
 - token bucket - countdown latch (tokens) and refilling scheduler 
 - leaking bucket - token bucket with a queue, requests in queue can get too old
 - fixed window counter - dict<timestamp, counter>, overcount when bursts around bucket edges
 - sliding window log - log requests with timestamp. flush out older than limit. high memory and logic to flush old timestamps
 - sliding window counter - take previous window into account. requests of current window + (% of previous window * requests of previous window)
