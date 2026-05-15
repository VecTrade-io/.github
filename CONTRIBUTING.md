# Contributing to VecTrade

Thank you for your interest in contributing to the VecTrade developer platform! This document provides guidelines for contributing to any repository in the VecTrade ecosystem.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Contribution Types](#contribution-types)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Commit Convention](#commit-convention)
- [CLA (Contributor License Agreement)](#cla)

---

## Code of Conduct

All contributors must adhere to our [Code of Conduct](CODE_OF_CONDUCT.md). We are committed to providing a welcoming and inclusive experience for everyone.

## Getting Started

1. **Fork** the repository you want to contribute to
2. **Clone** your fork locally
3. **Create a branch** from `main` for your changes
4. **Make changes** following our coding standards
5. **Test** your changes thoroughly
6. **Submit** a pull request

## Development Setup

### Prerequisites

| Tool | Version | Purpose |
|------|---------|---------|
| Python | 3.9+ | Python SDK, finkit |
| Node.js | 18+ | TypeScript SDK, docs |
| Go | 1.22+ | CLI |
| pnpm | 9+ | TypeScript package management |
| Docker | 24+ | Local services |

### Quick Setup

Each repository is self-contained. Fork and clone the specific package you want to contribute to:

```bash
# Python SDK / finkit
git clone https://github.com/<your-fork>/vectrade-python.git
cd vectrade-python
python -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
pytest

# TypeScript SDK / AI Provider
git clone https://github.com/<your-fork>/vectrade-node.git
cd vectrade-node
pnpm install
pnpm test

# CLI
git clone https://github.com/<your-fork>/vectrade-cli.git
cd vectrade-cli
go build ./...
go test ./...

# OpenAPI Spec
git clone https://github.com/<your-fork>/vectrade-openapi.git
cd vectrade-openapi
npx @stoplight/spectral-cli lint spec.yaml
```

## Contribution Types

| Type | Review SLA | Reviewer |
|------|-----------|----------|
| Documentation fix / typo | < 24 hours | Any maintainer |
| Example code / tutorial | < 48 hours | Any maintainer |
| Bug fix with test | < 48 hours | Package maintainer |
| New feature / method | < 1 week | Core team design review |
| `finkit` indicator | < 1 week | Core team + CLA required |
| Breaking change | RFC required | Core team vote |

## Pull Request Process

### Before Submitting

- [ ] Read the relevant package's `README.md` and `DEVELOPMENT.md`
- [ ] Ensure all tests pass (`./scripts/test-all.sh`)
- [ ] Lint and format your code
- [ ] Add tests for new functionality
- [ ] Update documentation if applicable
- [ ] Sign the CLA (first-time contributors)

### PR Requirements

1. **Title**: Follow [Conventional Commits](#commit-convention) format
2. **Description**: Explain what and why (not how — the code shows that)
3. **Tests**: All new code must have tests; maintain coverage thresholds
4. **Scope**: One concern per PR. Split large changes into smaller PRs.
5. **CI**: All checks must pass before review

### Review Process

1. Automated checks run (lint, test, type-check, coverage)
2. At least one maintainer reviews
3. Address feedback via new commits (do not force-push during review)
4. Maintainer squash-merges after approval

## Coding Standards

### Python (SDK + finkit)

- **Formatter**: `ruff format`
- **Linter**: `ruff check`
- **Type checker**: `mypy --strict`
- **Test framework**: `pytest`
- **Coverage**: ≥ 95%
- **Docstrings**: Google style
- **Imports**: sorted by `ruff` (isort-compatible)

### TypeScript (SDK + AI Provider)

- **Formatter**: `prettier`
- **Linter**: `eslint` (strict config)
- **Type checker**: `tsc --noEmit` (strict mode)
- **Test framework**: `vitest`
- **Coverage**: ≥ 90%
- **Style**: Prefer `const`, no `any`, no `as` casts unless justified

### Go (CLI)

- **Formatter**: `gofmt` / `goimports`
- **Linter**: `golangci-lint`
- **Test framework**: `go test`
- **Coverage**: ≥ 80%
- **Style**: Follow [Effective Go](https://go.dev/doc/effective_go)

### OpenAPI Spec

- **Linter**: Spectral (Redocly ruleset)
- **Breaking changes**: Detected by `oasdiff`
- **Format**: YAML (not JSON)

## Commit Convention

We use [Conventional Commits](https://www.conventionalcommits.org/) with the following scopes:

```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `test` | Adding/fixing tests |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `perf` | Performance improvement |
| `ci` | CI/CD changes |
| `chore` | Maintenance, dependencies |
| `breaking` | Breaking change (triggers major version bump) |

### Scopes

| Scope | Package |
|-------|---------|
| `python` | Python SDK |
| `typescript` | TypeScript SDK |
| `cli` | CLI |
| `mcp` | MCP Integration Kit |
| `finkit` | finkit library |
| `ai-provider` | Vercel AI SDK provider |
| `openapi` | OpenAPI specification |
| `docs` | Documentation |
| `examples` | Examples |
| `infra` | Infrastructure |

### Examples

```
feat(python): add streaming support for AI analysis endpoint
fix(typescript): handle rate limit headers with zero remaining
docs(openapi): add webhook event schemas
test(finkit): add property-based tests for RSI indicator
ci(python): add Python 3.13 to test matrix
```

## CLA

For contributions to `finkit` and core packages, you must sign our Contributor License Agreement. This is a one-time process:

1. First-time PRs will be flagged by our CLA bot
2. Sign the CLA by following the bot's instructions
3. Your signature is recorded — future PRs won't ask again

The CLA ensures that:
- You have the right to contribute the code
- VecTrade.io can distribute your contribution under the project license
- Your contribution is original work

---

## Questions?

- **GitHub Discussions**: For design questions and proposals → [VecTrade-io/.github Discussions](https://github.com/orgs/VecTrade-io/discussions)
- **Issues**: For bug reports and feature requests → file on the relevant repository

Thank you for helping make VecTrade better for developers everywhere! 🚀
