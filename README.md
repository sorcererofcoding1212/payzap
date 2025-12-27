# Payzap

A full-stack digital wallet application enabling real-time money transfers and interactive financial insights.

---

## Overview

Payzap is a full-stack digital wallet platform that allows users to send, receive,
and request money in real time.

The application supports peer-to-peer transfers along with simulated on-ramp and
off-ramp transactions through an integrated bank microservice. It is designed to
reflect real-world wallet and payment workflows while maintaining a clean and
scalable system architecture.

This repository serves as the **central documentation and entry point**
for the Payzap project.

---

## Links

- Live Application: https://payzap-app.onrender.com
- Main Application Repository: https://github.com/sorcererofcoding1212/payzap-app
- Webhook Repository: https://github.com/sorcererofcoding1212/payzap-webhook
- Bank Service Repository: https://github.com/sorcererofcoding1212/payzap-bank
- Realtime Service Repository: https://github.com/sorcererofcoding1212/payzap-ws

---

## Key Features

- **Authentication**  
  In-house authentication along with external providers such as Google and GitHub.

- **Peer-to-Peer Payments**  
  Users can send, receive, and request money with real-time updates.

- **On-Ramp & Off-Ramp Transactions**  
  A dedicated bank microservice simulates deposits and withdrawals
  to and from external accounts.

- **Real-Time Transfers & Requests**  
  P2P transfers and payment requests are processed with real-time
  status updates and notifications.

- **Interactive Dashboard & Analytics**  
  Users can view transaction history, analytics, and charts through
  an interactive dashboard with real-time notifications.

---

## Tech Stack

### Frontend
- Next.js
- TypeScript
- Tailwind CSS
- Shadcn UI
- Recharts

### Backend & Services
- Node.js
- Express
- TypeScript
- Prisma

### Database
- PostgreSQL

### Realtime
- WebSockets
  
---

## Architecture Overview

## Architecture Overview

Payzap follows a service-oriented architecture where responsibilities are
split across multiple independent services to improve isolation, security,
and maintainability.

The main Payzap application, built with Next.js, handles all **core business
logic**, including authentication, peer-to-peer transfers, payment requests,
and the initiation of on-ramp and off-ramp transactions. This service acts
as the primary system of record for user actions and wallet operations.

A separate **Bank Microservice**, also implemented as a Next.js application,
simulates real-world banking systems. It is responsible for handling bank-side
operations such as credential verification, balance checks, and debiting or
crediting bank accounts during on-ramp and off-ramp flows.

Instead of allowing the bank service to directly modify wallet balances,
a dedicated **Wallet Webhook Service** is used. This service is implemented
as an Express-based server and shares the same database as the main Payzap
application. The bank microservice communicates with this webhook, which
verifies transactions and safely updates wallet balances. This design
ensures that the core Payzap application remains isolated from external
service callbacks.

Real-time user notifications are handled by a lightweight **WebSocket
Service**. The main Payzap application connects to this service and emits
events whenever wallet or transaction-related actions occur. The WebSocket
service then delivers real-time notifications to connected clients.

This architecture closely mirrors real-world financial systems by separating
external integrations, core business logic, and real-time communication into
well-defined services.

---

## Repository Structure

Each Payzap service is maintained in a **separate repository** to allow
independent development and deployment.

This root repository exists to provide documentation, architectural context,
and direct access to all related codebases.
