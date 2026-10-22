# Architecture Overview

## Objective

Build an educational transaction-processing system that validates simulated transactions, produces explainable risk decisions, and records outcomes for later analysis.

## Initial synchronous path

1. A client submits a transaction to the Java Spring Boot API.
2. The API validates the request and applies explicit request and error semantics.
3. Decision orchestration invokes deterministic rules and, later, a model behind a stable interface.
4. The decision includes an outcome, score where appropriate, and reason codes.
5. Persistent decision and audit storage will be added after the API contract is established.

## Offline machine learning

Python will handle historical-data preparation, feature engineering, model training, evaluation, and model-quality checks. Training must avoid target leakage and use appropriate time-aware evaluation where needed.

## Future infrastructure

PostgreSQL is planned for durable decision records. Kafka may be introduced for asynchronous event processing after the synchronous baseline is tested. Redis is optional and requires a concrete latency or online-feature use case. Observability and automated CI tests will be introduced as the system grows.

## Current state

The Spring Boot application scaffold has been generated, and its initial Maven test passed locally. Fraud rules, production transaction contracts, database persistence, Kafka integration, and ML inference are not yet implemented.

## Non-goals for the initial milestone

- No live payment authorization.
- No real customer or banking data.
- No claim of production readiness or production-scale performance.
