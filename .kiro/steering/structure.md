# Project Structure & Organization

## Root Directory Layout
```
├── cmd/erpc/           # Main application entry point
├── erpc/              # Core eRPC server logic and HTTP handlers
├── common/            # Shared types, configs, and utilities
├── architecture/evm/  # EVM-specific blockchain architecture
├── upstream/          # Upstream provider management and failsafe
├── data/              # Database connectors and caching
├── auth/              # Authentication strategies and middleware
├── clients/           # HTTP/RPC client implementations
├── consensus/         # Consensus algorithms and policies
├── health/            # Health tracking and monitoring
├── telemetry/         # Metrics and observability
├── thirdparty/        # Third-party provider integrations
├── util/              # General utility functions
├── test/              # Integration tests and test utilities
├── typescript/        # TypeScript configuration and CLI tools
├── docs/              # Documentation (Next.js site)
├── monitoring/        # Grafana, Prometheus configs
└── kube/              # Kubernetes deployment manifests
```

## Code Organization Patterns

### Package Structure
- **Single responsibility**: Each package has a focused purpose
- **Layered architecture**: Clear separation between HTTP, business logic, and data layers
- **Dependency injection**: Components are injected rather than directly instantiated

### Key Architectural Components
- **ERPC**: Main server struct that orchestrates all components
- **ProjectsRegistry**: Manages multiple projects and their configurations
- **Network**: Represents blockchain networks with their upstreams
- **Upstream**: Individual RPC provider connections with failsafe policies
- **ConnectorConfig**: Database/cache connection configurations

### Configuration Hierarchy
1. **Global Config** (`common.Config`) - Server-wide settings
2. **Project Config** (`common.ProjectConfig`) - Project-specific settings
3. **Network Config** (`common.NetworkConfig`) - Network-specific settings
4. **Upstream Config** (`common.UpstreamConfig`) - Provider-specific settings

### Testing Structure
- **Unit tests**: `*_test.go` files alongside source code
- **Integration tests**: `test/` directory with full system tests
- **Benchmarks**: `*_bench_test.go` files for performance testing
- **Test utilities**: `test/util/` for shared test helpers

### File Naming Conventions
- **Go files**: `snake_case.go`
- **Test files**: `*_test.go`
- **Benchmark files**: `*_bench_test.go`
- **Mock files**: `*_mock.go` or `mock_*.go`
- **Config files**: `erpc.yaml`, `erpc.ts`, `erpc.js`

### Import Organization
- Standard library imports first
- Third-party imports second  
- Local project imports last
- Grouped with blank lines between sections

### Error Handling
- Custom error types in `common/errors.go`
- Structured error responses with consistent JSON-RPC format
- Error wrapping with context preservation
- Logging with structured fields using zerolog

### Configuration Management
- YAML as primary configuration format
- TypeScript/JavaScript support for dynamic configs
- Environment variable expansion in YAML
- Type-safe configuration with validation
- Default value handling in `SetDefaults()` methods