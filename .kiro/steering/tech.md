# Technology Stack & Build System

## Core Technologies
- **Language**: Go 1.23+ (primary backend)
- **TypeScript/JavaScript**: Configuration files and CLI tooling
- **Package Manager**: pnpm (for TypeScript components)
- **Build Tool**: Go modules + Make + esbuild

## Key Dependencies
- **HTTP Framework**: Custom HTTP server implementation
- **JSON Processing**: bytedance/sonic (high-performance JSON)
- **Caching**: dgraph-io/ristretto/v2
- **Database Drivers**: 
  - Redis: redis/go-redis/v9
  - PostgreSQL: jackc/pgx/v4
  - DynamoDB: aws/aws-sdk-go
- **Monitoring**: prometheus/client_golang
- **Tracing**: OpenTelemetry (go.opentelemetry.io/otel)
- **Testing**: testify/testify, testcontainers-go
- **CLI**: urfave/cli/v3
- **Logging**: rs/zerolog
- **Failsafe**: failsafe-go/failsafe-go
- **Crypto**: ethereum/go-ethereum, spruceid/siwe-go

## Build Commands

### Development
```bash
make setup          # Install Go dependencies
make run            # Run eRPC server locally
make run-pprof      # Run with profiling enabled
make run-fake-rpcs  # Run fake RPC servers for testing
```

### Testing
```bash
make test           # Run all tests with coverage and race detection
make test-fast      # Run tests without race detection (faster)
make test-race      # Run extensive race condition tests
make bench          # Run benchmarks
make coverage       # Generate test coverage report
```

### Building
```bash
make build          # Build production binaries (erpc-server, erpc-server-pprof)
make fmt            # Format Go code
```

### Docker & Infrastructure
```bash
make up             # Start docker-compose services
make down           # Stop docker-compose services
```

### Performance Testing
```bash
make run-k6-evm-tip-of-chain           # Run k6 performance tests (tip of chain)
make run-k6-evm-historical-randomized  # Run k6 performance tests (historical)
```

## Configuration
- **Primary Config**: YAML format (erpc.yaml, erpc.yml)
- **Alternative Config**: TypeScript/JavaScript (erpc.ts, erpc.js) 
- **Environment**: .env file support via godotenv
- **Type Generation**: tygo for Go-to-TypeScript type generation

## Code Quality Tools
- **Linting**: Biome (for TypeScript/JavaScript)
- **Formatting**: gofmt (Go), Biome (TS/JS)
- **Testing**: Go's built-in testing + testify assertions