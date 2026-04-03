# Integration testing (practice)

Deep notes on **integration testing** as a discipline: how you define it on your stack, where it sits in the test pyramid, and how you run it reliably in CI. This file is for **your** conventions—link out to team standards when they live elsewhere.

## What “integration” means here

Definitions vary. Capture **your org’s** definition in one paragraph:

- **Scope** — which boundaries count as “integrated” (e.g., service + DB, two services, service + queue + DB)?
- **Not integration** — what you explicitly exclude (full browser journeys, full production-like envs).

_Add your paragraph._

## Boundaries: unit vs integration vs end-to-end

| Layer | Typical focus | Your stack / notes |
|--------|----------------|-------------------|
| Unit | Isolated modules, mocks | |
| Integration | Real dependencies *within* a slice (DB, broker, other internal APIs) | |
| E2E / system | Full user or API journey across many components | |

Clarity here prevents **duplicate coverage** and arguments about who owns which failures.

## When integration tests earn their keep

- **Contracts** between teams or services need validation beyond mocks.
- **Persistence, messaging, or schema** behavior is risky to fake.
- **Regression** of cross-component behavior is cheaper to catch here than in long E2E runs.

## Design patterns you use

- Test **slices** (e.g., in-process + real DB) vs **full microservice graph**.
- **Testcontainers** (or similar) vs shared long-lived environments.
- **Data setup/teardown** — factories, migrations, transactions, truncation strategy.

_Add patterns and links to internal RFCs or example tests._

## Environments and CI

- Where integration tests run (every PR, nightly, main-only).
- **Parallelism**, **timeouts**, **flake** handling.
- Secrets and **external systems** — sandboxes, stubs, or no-go list.

## Anti-patterns to watch

- Integration suite that grows into a **slow, flaky E2E** substitute.
- **No ownership** when red—who fixes: service team, platform, QE?
- **Over-mocking** at this layer (then you are not testing integration).

## Tooling

Point to your concrete tools in [`../tools-and-tech-stack.md`](../tools-and-tech-stack.md); list only integration-specific choices here.

| Concern | Tool / approach | Notes |
|---------|-----------------|--------|
| DB | | |
| Messaging | | |
| HTTP / APIs | | |
| Orchestration | | |

## References (external)

| Resource | Why it matters |
|----------|----------------|
| | |

## Internal links

| Doc / repo | What it defines |
|------------|------------------|
| | |
