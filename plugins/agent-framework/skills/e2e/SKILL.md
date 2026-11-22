---
name: e2e
description: Analyze a repository and set up or improve emulator-free API and browser E2E testing with isolated test data and useful artifacts.
user-invocable: true
---

# Emulator-free E2E setup

Goal: make tests executable by a coding agent through CLI without requiring Android Emulator or iOS Simulator for the covered workflows.

1. Delegate repository discovery to `explorer` (Haiku): identify frontend/backend, package manager, existing tests, start commands, service dependencies and critical user journeys.
2. Ask `e2e-engineer` (Sonnet) to propose the smallest suitable test architecture before editing.
3. Prefer:
   - unit/integration tests for deterministic logic and module boundaries;
   - API E2E against a dedicated local/test backend and isolated database;
   - Playwright headless Chromium for browser-accessible UI;
   - existing test framework rather than introducing a competing stack.
4. For Expo/React Native, use Expo Web + Playwright only for shared UI and web-compatible flows. Do not represent this as native iOS/Android coverage.
5. Isolate test data. Require explicit test-only URLs and credentials. Never run against production.
6. Avoid fixed sleeps. Use state-based assertions, deterministic fixtures, independent tests and parallel-safe cleanup.
7. Capture logs, screenshots, Playwright traces and HTML reports on failure.
8. Delegate execution to `test-runner` (Haiku) and review test architecture/coverage with `reviewer` (Opus).

Native-only behavior still requires a real device or simulator at an appropriate validation stage, including IAP, push permission flows, Live Activities, camera, native modules, OS integrations and platform-specific navigation.

Deliver:
- architecture and rationale;
- install/setup commands verified against the repository;
- test scripts;
- test data and cleanup strategy;
- coverage boundaries and known limitations;
- actual test execution results.
