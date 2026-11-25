# Progress Log

One row is added every week (CEP Git rules). Commit links point to the main commit of that week's work.

| Week | Date | Work done | Who | Problems | Next step | Commit |
|---|---|---|---|---|---|---|
| 1 | 25 Nov 2026 | Repository created with README, .gitignore and folder skeleton. SRS v1.0 (numbered FRs, NFRs, use cases, constraints) and SDS v1.0 (architecture, class design, ERD, UI, error handling) added to `docs/`. Low-fidelity wireframes (9 screens) and PlantUML diagram sources added. Event chat module added to scope as requested at proposal approval. | Shaheer Zaib (SDS: architecture, database, error handling; diagrams), Fahad Ali Khan (SRS; wireframes; UI design) | Deciding between WebSockets and SSE for chat; chose SSE + REST so chat reuses the same auth, validation and error handling. | Week 2: database schema and seed script, Express skeleton with auth and roles, React layout and login pages. | _add link_ |
