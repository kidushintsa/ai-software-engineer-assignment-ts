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

are intentionally **not committed**.

---

# Bug Fix

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
