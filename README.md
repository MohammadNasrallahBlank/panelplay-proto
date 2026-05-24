# panelplay-proto

Protocol Buffer contracts for the PanelPlay platform.

## Contents

```
panelplay/v1/
  auth.proto          — AuthService (register, login, refresh, logout)
  subscription.proto  — SubscriptionService (tiers, Stripe checkout)
  character.proto     — CharacterService (extraction, retrieval)
  scene_cache.proto   — SceneCacheService (DRM token flow, signed URLs)

gen/panelplay/v1/     — Generated Go stubs (committed; do not edit manually)
```

## Usage

### Go (backend)
```go
import pb "github.com/MohammadNasrallahBlank/panelplay-proto/gen/panelplay/v1"
```
```
go get github.com/MohammadNasrallahBlank/panelplay-proto@latest
```

### Android
Add as a git submodule at `proto/` in the `panelplay-android` repo. The Gradle
protobuf plugin generates Android stubs from `.proto` sources at build time.

## Regenerating stubs

```bash
protoc \
  --proto_path=. \
  --go_out=gen --go_opt=paths=source_relative \
  --go-grpc_out=gen --go-grpc_opt=paths=source_relative \
  panelplay/v1/*.proto
```

Requires: `protoc`, `protoc-gen-go`, `protoc-gen-go-grpc`

## Repos

| Repo | Description |
|------|-------------|
| [panelplay-proto](https://github.com/MohammadNasrallahBlank/panelplay-proto) | This repo — API contracts |
| [panelplay-backend](https://github.com/MohammadNasrallahBlank/panelplay-backend) | Go gRPC server |
| [panelplay-android](https://github.com/MohammadNasrallahBlank/panelplay-android) | Android app + SDK |
