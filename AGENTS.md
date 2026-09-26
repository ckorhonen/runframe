# Runframe repository guide

`lib/` contains the runner, preview, and React components; `examples/` and fixtures exercise circuits, while scripts and worker code support CSS/build/runtime behavior. Follow the existing tscircuit integration and browser rendering patterns rather than replacing the runner architecture.

Use Bun and the tracked lockfile (`bun install --frozen-lockfile`). `bun run start` builds CSS and starts Cosmos/watch development. `bun run build` builds CSS, standalone artifacts, standalone preview, and the library. `bun run format:check` checks Biome formatting; CI also runs `bunx tsc --noEmit` and `bun test` even though there is no package test script. `bun run build:site` exports Cosmos/iframe assets and is distinct from the library build. Match the existing workflow tool version when reproducing CI.

For runner changes, use a bounded existing fixture and inspect actual schematic/PCB/preview output and errors in the browser; compilation alone does not prove a correct circuit preview. Remote imports, provider-backed work, ordering flows, and publishing commands such as `pkg-pr-new-release` have external effects. Keep them outside ordinary local validation unless the task authorizes them.

## Completing work

Carry the authorized change through the relevant checks and repair failures it causes. Make routine, reversible implementation choices using existing patterns; ask only when missing information, a material product decision, or an authorization boundary prevents the next step. Existing authorization remains valid within its scope. If blocked, name the exact action and missing prerequisite, retain concise evidence, and continue independent work.

Choose verification proportional to the change. For instructions or prose, inspect changed paths, links, and local instruction precedence and run `git diff --check -- <changed-paths>`; don't install dependencies or run the application solely for a prose edit. For behavior changes, exercise the affected behavior and applicable checks below, then broaden only for failures or unresolved risk. Report files changed, checks actually run and their results, commands only inspected, and remaining limitations. A build or source inspection alone does not prove runtime behavior. Continue through already-authorized follow-through; stop at explicit review checkpoints or boundaries requiring new authorization.
