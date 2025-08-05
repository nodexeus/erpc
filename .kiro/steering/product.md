# eRPC Product Overview

eRPC is a fault-tolerant EVM RPC proxy and re-org aware permanent caching solution built for read-heavy use-cases like data indexing and high-load frontend usage.

## Key Features
- **Fault tolerance**: Retries, circuit breakers, failovers, and hedged requests
- **Smart caching**: Local re-org aware cache to avoid redundant upstream calls
- **Rate limiting**: Configurable rate limits per upstream to control usage and costs
- **Method routing**: Automatic routing without worrying about provider method support
- **Unified error handling**: Consistent error codes across multiple providers
- **Authentication**: Supports basic auth, secrets, JWT, SIWE and more
- **Smart batching**: Aggregate multiple RPC or contract calls into one
- **Data integrity**: Multiple mechanisms to ensure accurate, up-to-date responses

## Architecture
- Multi-project support with network-specific configurations
- Upstream provider management with automatic failover
- Pluggable database backends (Memory, Redis, PostgreSQL, DynamoDB)
- Comprehensive monitoring and metrics via Prometheus
- OpenTelemetry tracing support

## Target Use Cases
- Data indexing applications
- High-load frontend applications
- RPC aggregation and load balancing
- Cost optimization for blockchain RPC calls