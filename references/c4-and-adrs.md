# C4 Diagrams and ADRs

## C4 levels to produce

Level 1, Context: the system as one box, plus users and external systems.
Level 2, Container: deployable units - SPA, API, DB, queue, cache - with the
relationships between them.

Levels 3 and 4 are out of scope for an initial landscape.

## Mermaid starter

```mermaid
flowchart LR
  user([User]) --> spa[Web SPA]
  spa -->|HTTPS JSON| api[API Service]
  api --> db[(Primary DB)]
  api --> cache[(Cache)]
  api --> queue[[Job Queue]]
  queue --> worker[Worker]
  api --> ext[Third-party APIs]
