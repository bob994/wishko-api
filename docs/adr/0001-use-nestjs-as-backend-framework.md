# 1. Use NestJS as the backend framework

Date: 2026-05-21

## Status

Accepted

## Context

We need to choose a Node.js framework for the Wishko API. The main candidates considered were:

- **Express.js** — minimal, unopinionated, the de facto standard for many years.
- **Fastify** — leaner and faster than Express, with a strong plugin system but still relatively unopinionated.
- **NestJS** — opinionated, modular framework inspired by Angular, built on top of Express (with optional Fastify adapter), targeted at enterprise applications.

Considerations driving the decision:

- I have prior experience with Express.js and want to learn something new rather than reuse what I already know.
- Fastify is leaner, but I specifically want an opinionated framework that imposes structure so I can learn how things "should" be done rather than inventing conventions from scratch.
- The framework should be suitable for enterprise-grade applications: dependency injection, modularity, testability, first-class TypeScript support, and a healthy ecosystem (validation, OpenAPI, queues, GraphQL, microservices).
- NestJS does not lock us out of Fastify — it ships a Fastify adapter, so we can switch the underlying HTTP engine later if performance demands it.

## Decision

Use **NestJS** as the backend framework for Wishko API, running on its default Express adapter for now.

## Consequences

**Positive**

- Opinionated structure (modules, controllers, providers, DI) accelerates onboarding and enforces consistency.
- Strong TypeScript integration and first-class support for testing, validation, OpenAPI, and other enterprise concerns.
- Learning opportunity: gain experience with a framework I have not used before.
- Migration to the Fastify adapter remains possible if raw HTTP performance becomes a bottleneck.

**Negative**

- Heavier abstraction layer and steeper learning curve compared to Express or Fastify directly.
- Performance ceiling is lower than bare Fastify; some overhead from DI and decorators.
- More framework-specific knowledge required (Nest's module system, lifecycle hooks, etc.) — less transferable than vanilla Express/Fastify patterns.
