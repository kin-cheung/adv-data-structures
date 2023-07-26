# System Design

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
