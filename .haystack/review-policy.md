# Review Policies

## Manual review for input/update internals
- **Paths**: `packages/react-dom-bindings/src/client/ReactDOMInput.js`, `packages/react-dom/src/__tests__/ReactDOMInput-test.js`
- **Severity**: high
- **Reason**: Small changes in low-level input update logic can silently cause broad performance regressions or behavior changes (for example extra DOM writes or radio/name/type edge cases) that unit tests may not fully cover across real browser behavior.

## Manual review for compiler semantic-preservation changes
- **Paths**: `packages/react-compiler/**`
- **Severity**: high
- **Reason**: Compiler lowering and memoization changes can pass tests while still altering JavaScript runtime semantics or evaluation ordering in edge cases, causing correctness regressions in user code.

## Instructions
- If a PR changes developer warning behavior (for example warning vs error logging level or suppression options), require human judgment on the tradeoff between developer guidance and tooling disruption.
- If a PR changes SSR hydration diagnostics or messaging, require human review to judge whether the change improves debuggability without adding misleading hints, excessive noise, or unacceptable development-time overhead.
