# System Design

## Requirements gathering
### 1. Functional requirements
 - Identify actors, user cases and user flows 
### 2. Non-functional requirements
 - measurable and testable
 - tradeoffs and feasibility
 - no one single architecture can serve all quality requirements
### 3. Limitations and boundaries
 - technical (programming languages), business (budget), regulatory/legal constraints
   - be aware of self-imposed constraints that can be removed or avoided
 - Loosely couple current constraints or dependencies

## General considerations
 - performance - single host, multi-threaded, distributed, multi-region, edge computing, CDN, caching
   - percentile distribution (measurability)
   - degradation point (latency vs throughout)
 - availability - load balancing, replication, master/slave, election
 - consistency - sync/async
 - monitoring - core feature monitoring, algorithem efficiency
 - scalability - vertical, horizontal and team scalability
 - fault tolerance - can be resolved by:
   1) failure prevention - eliminate single point of failure through replication and redundancy 
   2) failure detection and isolation - health monitoring
   3) recovery - stop traffic, restart, rollback
 - SLA (business and legal), SLOs and SLIs (engineers defined and users most care about)
 - recovery plan - 1) alerts 2) auto failovers/restarts/rollbacks/auto scaling and 3) predefined handbooks

## Big Data Architecture
 - Lambda architecture - combining batch-processing and real-time processing to serve different user queries
  - batch layer - use batch jobs to produce batch views
  - speed layer - use data streaming to produce real-time analysis
  - serve layer - base on user queries, it gets data from batch views or real-time views or the combination of the two

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
