What is Rate Limiter?
A Rate Limiter is a backend system component that controls how many requests a user or client can make within a fixed time period.
If the request count stays within the allowed limit, the request is accepted. If the limit is exceeded, the request is blocked temporarily.

Why this project?
Modern backend systems receive massive traffic continuously. Without proper control, excessive requests can overload servers and affect system stability.
A Rate Limiter helps control traffic, prevent abuse, and ensure fair usage across users.
This project helps understand:
backend traffic control
request throttling
scalability concepts
distributed systems basics

Problem Statement
Imagine an Instagram-like system receiving millions of requests continuously.
If users or bots send unlimited requests:
servers become overloaded
API latency increases
systems may crash under heavy traffic
The system needs a mechanism to restrict excessive requests within a specific time window.

Solution
A Rate Limiter tracks how many requests a user sends within a fixed time period.
If the request count is within the limit:
✔ request is allowed
If the request count exceeds the limit:
❌ request is rejected temporarily
This protects the backend system from overload and maintains stability.

High Level Workflow
Client Request
      │
      ▼
Rate Limiter
      │
      ▼
Check Request Count
      │
      ▼
Within Limit ?
   ┌───────────┐
   │           │
 YES          NO
   │           │
   ▼           ▼
Allow       Reject
Request     Request
Example Workflow
Keerthu sends login request
            │
            ▼
      Rate Limiter
            │
            ▼
 Check requests in last 1 minute
            │
            ▼
     Count = 2 / Limit = 3
            │
            ▼
        Allow Request ✔

Core Components
Client Request
Incoming API request from user.
Rate Limiter
Main component that decides whether to allow or reject requests.
Request Tracking Store
Stores request counts or timestamps for users.
Time Window
Defines duration limit (example: 1 minute).
Rate Limit Policy
Defines maximum allowed requests.
Allow Flow
Forwards valid requests to backend system.
Reject Flow
Blocks requests when limit is exceeded.
Cleanup Logic
Removes expired request data.

Data Structures Used
HashMap
Queue / Deque

Important Edge Cases
Burst traffic
Concurrent requests
Expired data cleanup
Time boundary handling

Failure Scenarios
System crash / restart
Concurrency issues
Distributed counter mismatch

Where it is used
API systems
Login systems
Social media platforms
Payment systems
Cloud services

Scaling Approach
To scale the system:
move from local memory to distributed cache
use shared request tracking across servers
make servers stateless

Implementation Coding Parts
RateLimiter
Request Store
Rate Limit Policy
allowRequest()
Time Window Logic
Request Counter Logic
Reject Request Logic
Cleanup / Expiry Logic

Final Goal
Build a backend traffic control system that demonstrates:

request throttling
backend scalability concepts
traffic management
distributed systems fundamentals
