# Eventide – NASCON Event Management System

Eventide is a web application for running NASCON (National Student Convention), the annual multi-university student event. It replaces spreadsheets and messaging groups with one system that **applies the event's rules automatically**: clash-free venue booking, capacity and team-size checks, verified payments, judge scoring with a live leaderboard, an in-event chat, sponsorships, accommodation and reports.

> SEL-311 Software Construction · Complex Engineering Problem · Bahria University Islamabad · Fall 2026

## Features

| Module | Priority | Highlights |
|---|---|---|
| User Management | Core | Sign-up, login (JWT), five roles: Admin, Organizer, Participant, Judge, Sponsor |
| Events & Venue Scheduling | Core | Events in 4 categories, rounds, criteria, clash-free venue booking |
| Registration | Core | Individual and team registration, seat holds, duplicate and size checks |
| Payments | Core | Server-computed fees, payment submission and staff verification |
| Judging | Core | Criteria scoring, averaged weighted scores, ranks, winners, live leaderboard |
| Event Chat | Core | Real-time chat per event for confirmed participants, organizer and judges |
| Live Updates | Core | Server-Sent Events for leaderboard, seats, chat and notifications |
| Sponsorship | Extended | Title / Gold / Silver / Bronze / Media Partner packages, deliverables |
| Accommodation | Extended | Gender-segregated automatic room allocation, check-in/out |
| Reports | Extended | Participation, venue utilisation, revenue, occupancy, results (CSV) |

## Technology

- **Frontend:** React (Vite), responsive UI
- **Backend:** Node.js 20 LTS, Express 4 — layered: routes → controllers → services → repositories
- **Database:** PostgreSQL 16 (`btree_gist` extension for the venue-clash constraint)
- **Real-time:** Server-Sent Events with polling fallback
- **Testing:** Jest + Supertest

## Repository Structure

```
client/      React front end
server/      Express API (src/routes, middleware, controllers, services, models, repositories, errors, live)
database/    schema.sql, seed.sql
docs/        SRS, SDS, diagrams (PlantUML), low-fidelity wireframes
```

## Getting Started

> Construction starts after Assignment 3 approval; these steps describe the planned setup.

### Prerequisites
- Node.js 20 LTS
- PostgreSQL 16

### Database setup
```bash
createdb eventide
psql -d eventide -c "CREATE EXTENSION IF NOT EXISTS btree_gist;"
psql -d eventide -f database/schema.sql
psql -d eventide -f database/seed.sql
```

### Environment
Copy `server/.env.example` to `server/.env` and fill in the values (never commit `.env`):
```
DATABASE_URL=postgres://<user>:<password>@localhost:5432/eventide
JWT_SECRET=<long random string>
CLIENT_ORIGIN=http://localhost:5173
PORT=4000
```

### Run
```bash
cd server && npm install && npm run dev     # API on http://localhost:4000
cd client && npm install && npm run dev     # UI on http://localhost:5173
```

### Tests
```bash
cd server && npm test
```

## Documentation

- [Software Requirements Specification](docs/Eventide_SRS.pdf)
- [Software Design Specification](docs/Eventide_SDS.pdf)
- [Low-fidelity wireframes](docs/wireframes/Eventide_LowFi_Wireframes.pdf)
- [Diagram sources (PlantUML)](docs/diagrams)
- [Progress log](PROGRESS_LOG.md)

## Screenshots

_Screenshots of the running website will be added during construction (Assignment 4)._

## Team

| Member | Enrollment No. | Main responsibility |
|---|---|---|
| Shaheer Zaib | 09-131242-103 | Server and database: Express API, PostgreSQL schema, authentication, business rules, API tests |
| Fahad Ali Khan | 09-131242-023 | Interface: React pages, forms and validation, live updates, prototypes, UI tests |

Instructor: Engr. Saad Mazhar Khan
