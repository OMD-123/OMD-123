# Daily Advance Backend Project Log

## 2026-08-16 — Day 1: Distributed Rate Limiter
**Repo:** https://github.com/OMD-123/advance-backend-day1-rate-limiter
**Stack:** Node.js/Express/TypeScript + Redis
**Features:**
- 5 algorithms: Token Bucket, Sliding Window Counter, Leaky Bucket, Fixed Window, Sliding Window Log
- Redis-backed distributed rate limiting with in-memory fallback
- Multiple limit tiers: per-IP, per-user, per-API-key, per-endpoint
- Standard rate limit headers (X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset, Retry-After)
- Express middleware factory
- Docker Compose with Redis
- Jest unit tests

## 2026-08-17 — Day 2: JWT Auth Microservice
**Repo:** https://github.com/OMD-123/advance-backend-day2-jwt-auth
**Stack:** Node.js/Express/TypeScript + Redis
**Features:**
- JWT Access + Refresh token rotation
- Role-Based Access Control (RBAC): admin, moderator, user, guest
- Permission-based authorization
- Token blacklisting (revocation)
- bcrypt password hashing (configurable rounds)
- Rate limiting on auth endpoints
- Express middleware for auth/roles/permissions
- Comprehensive TypeScript types

## 2026-08-17 — Day 3: GraphQL API Gateway
**Repo:** https://github.com/OMD-123/advance-backend-day3-graphql-gateway
**Stack:** Node.js/Express/TypeScript + GraphQL Yoga + Redis
**Features:**
- Schema stitching for multiple upstream services
- Two-level caching (L1 in-memory + L2 Redis)
- Sliding window rate limiting with Redis sorted sets
- JWT authentication (optional, public queries allowed)
- GraphQL Yoga server with GraphiQL playground
- Health checks and graceful shutdown

## 2026-08-18 — Day 4: Real-time Notification System
**Repo:** https://github.com/OMD-123/advance-backend-day4-notification-system
**Stack:** Node.js/Express/TypeScript + WebSocket + BullMQ + Redis
**Features:**
- WebSocket hub for real-time in-app notification delivery
- Redis pub/sub for cross-instance fan-out
- Multi-channel delivery: email, webhook, in-app, push
- Webhook retry (3 attempts, 5000ms timeout) with dead-letter queue
- JWT authentication for routes and WebSocket connections
- O(1) in-app inbox retrieval via Redis sorted sets
- 24 tests green

## 2026-08-19 — Day 5: Distributed Job Queue
**Repo:** https://github.com/OMD-123/advance-backend-day5-job-queue
**Stack:** Node.js/Express/TypeScript + BullMQ + Redis
**Features:**
- 4 queue types: mail, analytics, notifications, export
- Priority queuing — critical jobs jump the line
- Automatic retry with exponential backoff
- Dead-letter queue for failed jobs
- Scheduled/repeated jobs via BullMQ repeat
- Multi-worker concurrency
- REST API for enqueue, inspect, retry, bulk-add
- 45 tests green

---

Next: Day 6 — Backend System