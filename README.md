# Angular 21 Enterprise App — Engineering Baseline (2026)

> High-level standards for building and maintaining an enterprise-grade Angular application.
> Last reviewed: **2026-10-29** · Stack: **Angular 21.2 LTS · TypeScript 5.9 · Node 24**

## Table of contents

1. [Platform](#1-platform)
2. [Core concepts](#2-core-concepts)
3. [Structure](#3-structure)
4. [Architecture & state](#4-architecture--state)
5. [Quality](#5-quality)
6. [Security & compliance](#6-security--compliance)
7. [Performance & delivery](#7-performance--delivery)
8. [Tooling](#8-tooling)
9. [Governance](#9-governance)
10. [References](#references)

---

## 1. Platform

Angular 21.2 LTS (supported until June 2027), TypeScript 5.9, Node 24, `@angular/build` only.
Plan the move to **Angular 22 + Node 26 for Q1 2027**.

## 2. Core concepts

Zoneless + `OnPush`, signals for all component state, standalone components, built-in control flow (`@if` / `@for` / `@defer`), `inject()`, strict templates.
Signal Forms, `httpResource` and Angular Aria wait until Angular 22.

## 3. Structure

Use Lazy loading

## 4. Architecture & state

Signal-based services for feature and shared state (plain `signal` / `computed`, no NgRx). RxJS only for streams (websockets, debounce, cancellation), converted with `toSignal()`.
OpenAPI-generated API client, one ordered interceptor chain, global error handler, runtime config and feature flags exposed as signals.

## 5. Quality

angular-eslint on ESLint 10, Prettier, Vitest + Testing Library, Playwright + axe, bundle budgets and coverage thresholds — all blocking in CI. Renovate for dependencies.

Local enforcement before code reaches CI: Husky git hooks with lint-staged (`eslint --fix` + `prettier --write` on staged files at `pre-commit`) and commitlint (`@commitlint/config-conventional` at `commit-msg`) so conventional commits feed semantic-release. Sheriff boundary checks run in the same lint pass.

## 6. Security & compliance

Nonce-based CSP with Trusted Types, OIDC via BFF (httpOnly cookie), no tokens in `localStorage`, lockfile + SBOM + audit gates, WCAG 2.2 AA, Transloco for FR/EN, Law 25 consent gating all telemetry.

## 7. Performance & delivery

CSR for internal apps, SSR only for public/SEO surfaces. `@defer` and `NgOptimizedImage`, hashed assets with immutable caching, multi-stage Docker on `node:24-slim`, semantic-release.

## 8. Tooling

Angular Material 3 with design tokens, Angular DevTools, Angular Agent Skills, and an `AGENTS.md` carrying the project constraints.

## 9. Governance

ADRs for the six big choices, a short coding-standards doc, a quarterly upgrade owner, and a rule that experimental APIs require an ADR with a removal date.

---

## References

- [Angular releases & support policy](https://angular.dev/reference/releases)
- [Angular version compatibility](https://angular.dev/reference/versions)
- [Angular style guide](https://angular.dev/style-guide)
- [Angular security best practices](https://angular.dev/best-practices/security)
- [Angular AI best practices & Agent Skills](https://angular.dev/ai)
- [Node.js release schedule](https://github.com/nodejs/Release)
