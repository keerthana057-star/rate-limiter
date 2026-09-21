Distributed Redis-Backed API Rate Limiter

A Rate Limiter is a backend system component that controls how many requests a user or client can make within a specific time period. If the request stays within the allowed limit, it is accepted. If the limit is exceeded, the request is temporarily rejected.

Why This Project?

Modern backend systems receive large volumes of requests continuously. Without proper traffic control, excessive requests can overload servers, increase latency, and affect system stability.

This project helps understand:

* Backend traffic control
* Request throttling
* Scalability
* Distributed systems fundamentals

Problem Statement

Imagine an Instagram-like system receiving millions of requests continuously.

If users or bots send unlimited requests:

* Servers can become overloaded
* API latency can increase
* System stability can be affected
* Backend resources can be exhausted

The system needs a mechanism to restrict excessive requests within a specific time period.

Solution

The Rate Limiter tracks requests from each user and determines whether a new request should be allowed or rejected based on the configured rate limit.

```text
Request
   ↓
Rate Limiter
   ↓
Check Request Limit
   ↓
Within Limit?
   ├── YES → Allow Request
   └── NO  → Reject Request
```

High-Level Workflow

```text
Client Request
      ↓
Rate Limiter
      ↓
Request Tracking
      ↓
Rate Limit Check
      ↓
Allow / Reject
      ↓
Backend Service
```

Example Workflow

```text
Keerthu sends API request
        ↓
Rate Limiter
        ↓
Check requests in the configured time window
        ↓
Count = 2 / Limit = 3
        ↓
Allow Request ✓
```

Core Components

Client Request — Incoming API request from a user.
Rate Limiter — Decides whether a request should be allowed or rejected.
Request Tracking Store — Stores request counts or timestamps.
Time Window — Defines the duration over which requests are limited.
Rate Limit Policy — Defines the maximum number of allowed requests.
Allow Flow— Forwards valid requests to the backend service.
Reject Flow — Blocks requests when the limit is exceeded.
Cleanup Logic — Removes expired request data.

Data Structures Used

* HashMap
* Queue / Deque

Important Edge Cases

* Burst traffic
* Concurrent requests
* Expired data cleanup
* Time boundary handling

Failure Scenarios

* System crash / restart
* Concurrency issues
* Distributed counter mismatch

Where It Is Used

* API systems
* Login systems
* Social media platforms
* Payment systems
* Cloud services

Scaling Approach

To scale the Rate Limiter:

* Move request tracking from local memory to a distributed cache
* Share request state across multiple servers
* Keep application servers stateless

Implementation Coding Parts

* RateLimiter
* Request Store
* Rate Limit Policy
* `allowRequest()`
* Time Window Logic
* Request Counter Logic
* Reject Request Logic
* Cleanup / Expiry Logic

Final Goal

Build a backend traffic-control system that demonstrates:

* Request throttling
* Backend scalability
* Traffic management
* Distributed systems fundamentals

