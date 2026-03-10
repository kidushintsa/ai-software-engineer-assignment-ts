# AI Experts Assignment (JS/TS)

This assignment evaluates your ability to:

- set up a small JavaScript/TypeScript project to run reliably (locally + in Docker).
- Pin dependencies for reproducible installs.
- Write focused tests to reproduce a bug.
- Implement a minimal, reviewable fix.

---

# Running the Project Locally

### 1. Install dependencies

```bash
npm install
```

### 2. Run the test suite

```bash
npm test
```

The test suite runs using **Vitest**.
All tests should pass after the bug fix has been applied.

---

# Running Tests Using Docker

Docker allows the test suite to run in a clean environment similar to a CI pipeline.

### 1. Build the Docker image

```bash
docker build -t ai-software-engineer-assignment-ts .
```

### 2. Run the tests inside the container

```bash
docker run ai-software-engineer-assignment-ts
```

The container automatically runs:

```bash
npm test
```

This ensures the project works without any manual setup.

---

# Dependency Management

All dependencies are pinned using **exact versions** in `package.json`.

Example:

```
"vitest": "1.6.0"
```

Pinning versions prevents version drift and ensures reproducible installs.

Lockfiles such as:

- `package-lock.json`
- `yarn.lock`
- `pnpm-lock.yaml`

are intentionally **not committed**, as required by the assignment.

---

# Bug Fix

A bug existed in the OAuth2 token handling logic inside the HTTP client.

The issue occurred when the stored token was a **plain object** rather than an instance of `OAuth2Token`.
Because the refresh logic relied on an `instanceof` check, the client failed to refresh the token in that scenario.

The fix ensures that tokens which are not valid `OAuth2Token` instances are refreshed properly.

A detailed explanation is provided in:

```
EXPLANATION.md
```

---

# Project Structure

```
src/
  httpClient.ts
  tokens.ts

tests/
  httpclient.test.ts

Dockerfile
README.md
EXPLANATION.md
package.json
tsconfig.json
.gitignore
```

---

# Assignment Requirements

## Dockerfile

- The Docker image installs dependencies using `npm install`.
- The container runs the test suite by default using:

```
CMD ["npm", "test"]
```

## Dependency Pinning

- All dependencies use exact versions (`x.y.z`).
- No lockfiles are committed.

## Bug Fix

- The bug was identified using the test suite.
- A minimal change was applied to fix the issue.
- No unrelated refactoring was performed.

---

# Submission

This repository is submitted as a **public GitHub repository** containing:

- Source code
- Test suite
- Docker configuration
- Bug explanation
- Instructions for running the project locally and with Docker
