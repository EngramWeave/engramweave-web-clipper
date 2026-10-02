This repository is a maintained fork of Obsidian Web Clipper.

Preserve upstream behavior. Prefer additive changes over rewrites.

Do not replace upstream extraction/template/preview/highlight/save pipelines when they can be extended.

Reuse existing upstream logic and extension points whenever practical instead of implementing parallel custom versions.

Follow the upstream testing style, structure, scope, and level of coverage.

Keep EngramWeave-specific tests minimal and focused on important regression risks. Do not add redundant, speculative, exhaustive, or coverage-driven tests.

Do not introduce new testing frameworks, large test infrastructure, or broad E2E suites unless explicitly required.

Development may run on Windows. Upstream fixture tests have platform-sensitive line-ending and timezone assumptions.

When an authoritative upstream regression check is needed, run the existing test suite in an upstream-compatible environment with LF line endings and `TZ=America/Los_Angeles`.

Do not modify upstream tests or fixtures merely to accommodate local platform differences.