# Rate Limiter

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

## Core Entities
1. Rules
2. Requests
3. Clients

## System Interface
```java
isRequestAllowed(clientId, ruleId) -> (boolean, remaining : long, resetTime : timestamp)
```
## [Low Level Design](https://github.com/svetanis/low-level-design/tree/master/src/main/java/com/svetanis/ood/ratelimiter)

## [High Level Design](https://github.com/svetanis/system-design/blob/main/rate-limiter/RateLimiter-HLD.png)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/rate-limiter/diagram.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/rate-limiter/slides.pdf)

## [NotebookLM DeepDive Conversation](https://github.com/svetanis/system-design/blob/main/rate-limiter/audio.m4a)