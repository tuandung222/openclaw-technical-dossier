# 30 - Call Flow Catalog By File Function

## CF-1 CLI bootstrap to command execution

- `src/entry.ts`: env normalization + respawn policy + profile arg parsing
- `src/index.ts`: runtime guard + `buildProgram()`
- `src/cli/program.ts`: command routing
- `src/commands/*`: concrete command handlers

```mermaid
sequenceDiagram
  participant E as entry.ts
  participant I as index.ts
  participant P as cli/program.ts
  participant C as commands/*

  E->>E: normalizeEnv()
  E->>E: ensureExperimentalWarningSuppressed()
  E->>I: import runCli(argv)
  I->>I: assertSupportedRuntime()
  I->>P: buildProgram()
  P->>C: parseAsync + dispatch command
```

## CF-2 Gateway request lifecycle

- `src/gateway/server.impl.ts`: runtime composition
- `src/gateway/server-methods.ts`: authorization + handler dispatch
- `src/gateway/server-methods/*`: method implementations

```mermaid
sequenceDiagram
  participant Client
  participant GW as gateway ws/http
  participant Auth as authorizeGatewayMethod
  participant H as method handler

  Client->>GW: request(method, params)
  GW->>Auth: role+scope check
  Auth-->>GW: allow/deny
  alt allow
    GW->>H: invoke handler
    H-->>GW: result/error
    GW-->>Client: response
  else deny
    GW-->>Client: invalid_request + missing scope
  end
```

## CF-3 Agent run with fallback

- `src/agents/pi-embedded-runner/run.ts`: run orchestrator
- `src/agents/model-fallback.ts`: candidate sequencing and retries
- `src/process/command-queue.ts`: lane scheduling

```mermaid
sequenceDiagram
  participant Caller
  participant Q as command queue
  participant R as runEmbeddedPiAgent
  participant F as model-fallback

  Caller->>Q: enqueue session/global lanes
  Q->>R: execute run
  R->>R: resolve hooks and model
  R->>F: execute with fallback chain
  F-->>R: success or exhausted failure
  R-->>Caller: final payload/error
```

## CF-4 Tool policy to execution

- `src/agents/pi-tools.ts`: tool assembly
- `src/agents/tool-policy-pipeline.ts`: layered filtering
- `src/agents/sandbox/*`: sandbox overlays

Flow:

1. Build declared tools
2. Apply policy pipeline (profile -> group)
3. Apply sandbox overlays
4. Gate by approval if required
5. Execute tool

## CF-5 Memory search path

- `src/memory/manager.ts`: search orchestration
- `src/memory/hybrid.ts`: merge pipeline
- `src/memory/mmr.ts`, `src/memory/temporal-decay.ts`: optional ranking stages

Flow:

1. Check provider availability
2. If provider absent: query expansion + FTS-only
3. Else: vector + keyword retrieval
4. Merge weighted scores
5. Optional decay and MMR
6. Return top-k

## CF-6 Plugin channel registration path

- `src/plugins/loader.ts`: discovery + load + registry build
- `extensions/*/index.ts`: plugin register entry
- `src/channels/plugins/index.ts`: runtime list/dedupe/sort

Flow:

1. Discover plugin candidates
2. Validate manifest/config schema
3. Execute plugin register callback
4. Register channels/methods/tools/hooks
5. Expose through gateway and runtime adapters
