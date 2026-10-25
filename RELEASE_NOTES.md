# Release Notes

## v1.0.3
GH#1100 migration wave (batch 4) — stop naming a step that belongs to the consumer.

The body read `{{steps.Competitive Consolidation.output}}` — a step title that exists in the consuming workflow, not here. That is position-dependence across a reuse boundary in its most brittle form: the prompt only worked in a consumer that happened to have a step with that title, and would have bound silently to the wrong value in one that had a different step wearing the same name.

It now reads `{{step.context.source}}` and declares `source` as **required**. The consumer wires it with `bindings: { source: { from_step: "Competitive Consolidation" } }` — the name stays, but it becomes the consumer's statement about its own steps.

Reach verified before migrating: the named step exists and runs EARLIER than this prompt's step in its one consumer, so the value it receives is unchanged.

## v1.0.2
GH#657 Framing B — republish wave. Bundle now ships `dependencies: []` in its signed manifest (injected by `publish-skrpt.mjs` for `--shared` publishes), so the App's dep-referenced install pipeline (post-PR #47) accepts it on standalone update via Hub Update-all. No content changes.

## v1.0.1
GH#645 Row 3a — republish with `manifest.id` aligned to Hub catalog UUID. Pre-K-037 v1.0.0 bundle carried a local `manifest.id` that drifted from the catalog UUID. Row 5 (`0d9c9dbe`) reconciled the source file but not the signed bundle; v1.0.1 ships the corrected `manifest.id` so the batch-of-81 consumer migrations (GH#645 Row 3b) can pin this version and pass engine STEP 4d. No content changes.

## v1.0.0
Initial catalog release as independent shared object (GH#625 Step 2; canonical pick + rename surface per audit).
