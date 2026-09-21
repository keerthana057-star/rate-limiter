Redis-Backed API Rate Limiter

A Java-based API Rate Limiter built using the Token Bucket algorithm and Redis to control request rates and protect backend services from excessive traffic.

Project Goal

The goal of this project is to understand how rate limiting works in distributed systems and how shared rate-limit state can be maintained across multiple application instances.

The project focuses on:

* Token Bucket algorithm
* Token refill logic
* Request consumption
* Allow / Reject decisions
* Redis-based shared state
* Atomic operations
* Redis Lua scripting
* TTL and key expiration
* HTTP 429 responses
* Redis failure handling
* Unit, concurrency, and integration testing

🏗️ Architecture

```text
                  Client
                     │
                  Request
                     │
          Request Filter / Interceptor
                     │
                     ▼
            Rate Limiter Service
                     │
              Check Rate Limit
                     │
                     ▼
                  Redis
             Client Bucket State
                     │
              Atomic Operation
                     │
                Redis Lua
                     │
              ┌──────┴──────┐
              │             │
            ALLOW         REJECT
              │             │
              ▼             ▼
           Backend       HTTP 429
                         + Headers
```

 🪣 Token Bucket Flow

```text
Request
   ↓
Identify Client
   ↓
Get Bucket State
   ↓
Calculate Elapsed Time
   ↓
Refill Tokens
   ↓
Check Available Tokens
   ↓
Token Available?
   ├── YES → Consume Token → ALLOW
   │
   └── NO  → REJECT → HTTP 429
```

🧩 Components

1. Rate Limiter Configuration
2. Token Bucket
3. Token Refill Logic
4. Token Consumption
5. Allow / Reject Decision
6. Redis Connection
7. Redis Key & State Storage
8. Atomicity / Race Condition Handling
9. Redis Lua Script
10. TTL / Key Expiration
11. Rate Limiter Service
12. Request Filter / Interceptor
13. HTTP 429 + Rate-Limit Headers
14. Redis Failure Handling
15. Unit & Concurrency Testing
16. Integration Testing

🛠️ Tech Stack

* Java
* Maven
* Redis
* Redis Lua
* REST APIs
* HTTP
* Concurrency
* Data Structures

🔐 Key Design Concepts

 Token Bucket

Each client has a bucket with:

* Maximum capacity
* Current token count
* Token refill rate
* Last refill timestamp

Redis

Redis stores the shared bucket state so that multiple application instances can enforce the same rate limit.

Atomicity

Rate-limit state updates must be atomic to prevent multiple concurrent requests from consuming the same token incorrectly.

Lua Script

Redis Lua scripting is used to perform the rate-limit check and state update as one atomic operation.

TTL

Inactive client keys are automatically removed from Redis after their TTL expires.

Request Decision

```text
Request
   ↓
Rate Limiter
   ↓
Token Available?
   │
   ├── Yes → Consume Token → Continue Request
   │
   └── No  → HTTP 429 Too Many Requests
```

🧪 Testing

The project will include:

* Unit testing
* Token refill testing
* Allow / reject testing
* Concurrent request testing
* Redis integration testing
* End-to-end integration testing

 🚧 Project Status

In Development:

The project is being implemented component-by-component, with each component understood, implemented, tested, and integrated into the complete rate-limiting system.

Learning Objective

This project is primarily built as a hands-on learning project to understand:

* Rate-limiting algorithms
* Distributed state management
* Concurrency
* Race conditions
* Atomic operations
* Redis
* API-level protection
* Fault handling


