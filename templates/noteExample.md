# WebLogic Graceful Shutdown

## TL;DR
Graceful shutdown stops new requests and waits for ongoing work before stopping server.

## Why
To prevent data loss and incomplete transactions

## Key Concepts
- In-flight requests
- Transactions
- Timeout

## How it works
- Stop accepting new work
- Wait for existing threads
- Force shutdown if timeout exceeds

## Mistakes
- Thought shutdown is instant
- Ignored timeout behavior

## When to use
- Production restart
- Deployment