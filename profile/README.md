# MuniPrioritise

**Equity-Aware Municipal Service Request Management**

A research prototype connecting citizen reporting, algorithmic prioritisation, and field worker dispatch for South African municipalities — with socioeconomic equity built into the prioritisation engine.

> ITDMA3-22 Capstone · Eduvos · Software Engineering · 2026

---

## The Problem

Municipal dispatch systems default to efficiency-first logic — closest worker, easiest job, shortest route. In practice this means historically disadvantaged areas, which often have the most severe service failures, are systematically deprioritised. South African municipalities are constitutionally mandated to deliver services equitably. Most of their tooling works against that mandate.

## What We're Building

A mobile-first system with three components working together:

- **Resident app** — citizens report water, electricity, road, refuse, and sanitation issues from their phones with photos and GPS
- **Worker app** — field workers receive prioritised job assignments and update status in real-time
- **Supervisor dashboard** — managers monitor, override, and analyse service delivery across wards

The research contribution is a **hybrid equity-aware prioritisation algorithm** that makes the trade-off between operational efficiency and socioeconomic equity explicit and tunable, grounded in ward-level SAMPI data from StatsSA.

## Repositories

| | |
|---|---|
| [`mobile`](./mobile) | React Native + Expo — resident and worker apps |
| [`dashboard`](./dashboard) | React + Vite + Tailwind — supervisor web app |
| [`backend`](./backend) | Node.js + Express — REST API |
| [`algorithm`](./algorithm) | Python + FastAPI — prioritisation microservice |
| [`database`](./database) | PostgreSQL + PostGIS — schema and seed data |
| [`docs`](./docs) | API reference and architecture |

## The Algorithm

The hybrid algorithm combines an efficiency score (severity, wait time, proximity) with an equity score (ward deprivation index from SAMPI) into a single tunable formula:

```
final_score = (1 - α) × efficiency + α × equity
```

`α = 0` is pure efficiency. `α = 1` is pure equity. Default is `α = 0.4`. The system benchmarks this against FCFS, Greedy, and a Genetic Algorithm across equity metrics (Gini coefficient, low-income ward coverage) and efficiency metrics (average response time, high-severity response rate).

## Stack

React Native · Node.js · PostgreSQL + PostGIS · Python FastAPI · React + Tailwind

---

*Research prototype using synthetic data based on StatsSA / SAMPI 2022. Not connected to live municipal systems.*