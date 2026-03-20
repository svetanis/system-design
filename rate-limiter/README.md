# Design a Distributed Rate Limiter
A rate limiter controls how many requests a client can make within a specific timeframe.

## Functional Requirements
1. The system should identify clients by user ID, IP address, or API key 
to apply appropriate limits.
2. The system should limit HTTP requests based on configurable rules
(e.g., 100 API requests per minute per user).
3. When limits are exceeded, the system should reject with HTTP 429
and include helpful headers (rate limit remaining, reset time)

## Non-Functional Requirements
1. high availability over strong consistency. 
eventual consistency is ok.
2. low latency (< 5ms)
3. system scale: support 1M rps across 10M DAU

## System Interface
```java
isRequestAllowed(clientId, ruleId) -> (boolean, remaining : long, resetTime : timestamp)
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/rate-limiter/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/rate-limiter/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/rate-limiter/diagram.png)
