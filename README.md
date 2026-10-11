# CareBridge System — Unified Public Healthcare Platform

[![Backend Tests](https://img.shields.io/badge/Backend%20Tests-77%2F77%20Passing-brightgreen?style=flat-square)](https://github.com/MOULEESHWARAN-S31/CareBridge_System)
[![Flutter Tests](https://img.shields.io/badge/Flutter%20Tests-120%2F120%20Passing-brightgreen?style=flat-square)](https://github.com/MOULEESHWARAN-S31/CareBridge_System)
[![Flutter Analyze](https://img.shields.io/badge/Flutter%20Analyze-0%20Issues-brightgreen?style=flat-square)](https://github.com/MOULEESHWARAN-S31/CareBridge_System)
[![Node.js](https://img.shields.io/badge/Node.js-v18%2B-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16%2B-4169E1?style=flat-square&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?style=flat-square&logo=flutter&logoColor=white)](https://flutter.dev/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**CareBridge** is an integrated public healthcare platform designed to connect patients, hospitals, healthcare administrators, and government health departments through one digital ecosystem.

The platform brings together patient services, hospital management, healthcare facility administration, and public-health monitoring through a centralized backend and role-based dashboards.

## Table of Contents

- [Overview](#overview)
- [System Architecture](#system-architecture)
- [Modules and Technologies](#modules-and-technologies)
- [Key Features](#key-features)
- [Installation and Setup](#installation-and-setup)
- [Running the Applications](#running-the-applications)
- [Testing](#testing)
- [Project Structure](#project-structure)
- [Security](#security)
- [Maintainer and Project Partner](#maintainer-and-project-partner)
- [License](#license)

## Overview

CareBridge aims to improve access to public healthcare services and simplify coordination between citizens, hospitals, and government healthcare departments.

### Project Objectives

- Make healthcare services and facility information easier to access.
- Support digital OPD appointment booking and patient health-record management.
- Improve coordination of hospital operations and staff workflows.
- Provide district-level healthcare monitoring and disease-surveillance information.
- Implement role-based access for administrative and healthcare personnel.
- Support multilingual interfaces and offline-friendly experiences where implemented.

## System Architecture

```text
┌───────────────────────────────────────────────────┐
│                 CAREBRIDGE SYSTEM                 │
├───────────────────────────────────────────────────┤
│                                                   │
│  Patient App             Common Login Portal      │
│  Flutter                 HTML / CSS / JavaScript  │
│                                                   │
│  Admin Dashboard         Government Dashboard     │
│  JavaScript / CSS        React / TypeScript       │
│                                                   │
│  Hospital Management Dashboard                    │
│  React / JavaScript                               │
│                                                   │
└──────────────────────┬────────────────────────────┘
                       │
                       ▼
            ┌────────────────────────┐
            │ Unified REST API       │
            │ Node.js + Express      │
            │ JWT Authentication     │
            │ Role-Based Access      │
            └────────────┬───────────┘
                         │
                         ▼
            ┌────────────────────────┐
            │ PostgreSQL Database    │
            │ Centralized Data       │
            │ Relational Tables      │
            └────────────────────────┘
```

### Architectural Principles

1. **Centralized Data Access:** Frontend applications communicate with PostgreSQL through the backend REST API.
2. **Secure Configuration:** Database credentials and secrets are configured through environment variables.
3. **Role-Based Access Control:** Protected operations are authorized on the backend, with frontend route guards providing an additional layer.
4. **Unified Login:** A common login portal authenticates staff and redirects them according to their assigned roles.
5. **Modular Design:** Separate applications serve patients, administrators, government officials, and hospital staff.

## Modules and Technologies

| Module | Technology | Port |
|---|---|---:|
| Common Login Portal | HTML5, CSS3, JavaScript | 3000 |
| Admin Dashboard | JavaScript, CSS, SheetJS | 5173 |
| Government Dashboard | React, Vite, TypeScript | 5174 |
| Hospital Dashboard | React, Vite, Recharts | 5175 |
| Patient Application | Flutter, Dart | 8080 |
| Backend API | Node.js, Express, PostgreSQL client | 5000 |
| Database | PostgreSQL | 5432 |

## Key Features

### 1. Patient Application

- ABHA-related registration and profile workflows.
- Doctor and healthcare facility discovery.
- Location-based facility filtering.
- OPD appointment booking and token tracking.
- Patient health records, diagnostic reports, and prescriptions.
- Prescription-based medicine-order workflows.
- English, Tamil, and Hindi localization.
- Emergency SOS and emergency-facility discovery workflows.

### 2. Hospital Management System

Supports role-specific workflows for:

- Hospital administrators
- Doctors
- Nurses
- Receptionists
- Laboratory staff
- Pharmacists
- Billing staff
- Medical records staff
- Emergency staff
- HR managers

Other capabilities include bed occupancy monitoring, patient search, appointment tracking, and role-based dashboard access.

### 3. Government Health Dashboard

- District-level healthcare indicators.
- Disease-surveillance dashboards.
- Monitoring of diseases such as dengue, typhoid, malaria, and influenza.
- Hospital bed and ICU resource monitoring.
- Public-health trend analysis and predictive views where implemented.

### 4. Admin Dashboard

- Healthcare facility registration and management.
- Hospital and pharmacy directory management.
- Staff account administration.
- Medicine inventory management.
- Bulk data imports using spreadsheet files.
- Administrative audit logging where configured.

### 5. Common Login Portal

- Centralized staff authentication.
- JWT-based authentication.
- Role-based redirection to the appropriate dashboard.
- Access control for administrative and hospital roles.
- Demo workflows for project evaluation.

### 6. Backend and Database

- REST API built with Node.js and Express.
- PostgreSQL relational database.
- Password hashing using bcrypt.
- JWT authentication and authorization middleware.
- Parameterized SQL queries.
- Centralized database access and transactional operations where implemented.

## Installation and Setup

### Prerequisites

Install the following tools:

- Node.js v18 or newer
- PostgreSQL v16 or newer
- Flutter SDK v3.19 or newer
- Git
- Google Chrome for browser-based testing

### Step 1: Clone the Repository

```bash
git clone https://github.com/MOULEESHWARAN-S31/CareBridge_System.git
cd CareBridge_System
```

If you are using a separate fork or copy of the project, clone that repository instead.

### Step 2: Configure Environment Variables

Create a local `.env` file from `.env.example`.

On Windows Command Prompt:

```bat
copy .env.example .env
```

Example development configuration:

```env
PORT=5000
NODE_ENV=development
DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@localhost:5432/carebridge_db
JWT_SECRET=replace_with_a_long_random_secret
JWT_EXPIRES_IN=24h
CORS_ORIGIN=*
```

Replace the example database password and JWT secret with your own values.

**Important:** Never commit your `.env` file, real credentials, or production secrets to GitHub. Production deployments should use a restricted CORS configuration and securely managed secrets.

### Step 3: Install Dependencies

Run the following commands from the repository root, adjusting directory names to match your checkout:

```bash
npm install
npm --prefix backend install
npm --prefix ADMIN_DASHBOARD install
npm --prefix GOVERNMENT_DASHBOARD install
npm --prefix HOSPITAL_DASHBOARD install
```

Install Flutter dependencies:

```bash
cd CARE_BRIDGE
flutter pub get
cd ..
```

### Step 4: Initialize the Database

Ensure PostgreSQL is running and your environment variables are configured.

Run the project's database setup commands:

```bash
npm --prefix backend run db:setup
node backend/scripts/seed_hospital_roles.js
```

Run the second command only if that script exists in your checkout and is intended for your local development database.

Use demonstration data for testing rather than real patient information.

## Running the Applications

### Start the Web Services

From the project root, run the startup script defined in your `package.json`:

```bash
npm start
```

Depending on your repository configuration, alternatives may include:

```bash
npm run dev
npm run dev:all
```

### Local URLs

| Service | URL |
|---|---|
| Common Login | http://localhost:3000 |
| Backend API | http://localhost:5000 |
| Admin Dashboard | http://localhost:5173 |
| Government Dashboard | http://localhost:5174 |
| Hospital Dashboard | http://localhost:5175 |
| Patient Application | http://localhost:8080 |

### Start the Flutter Patient Application

Open a separate terminal:

```bash
cd CARE_BRIDGE
flutter run -d chrome --web-port=8080
```

Open http://localhost:8080 in your browser.

### Run Individual Modules

Use the scripts defined in each `package.json`.

| Command | Purpose |
|---|---|
| `npm run dev:backend` | Start the backend |
| `npm run dev:login` | Start the login portal |
| `npm run dev:admin` | Start the admin dashboard |
| `npm run dev:gov` | Start the government dashboard |
| `npm run dev:hospital` | Start the hospital dashboard |
| `npm run dev:carebridge` | Start the Flutter application |

**Note:** Confirm that these script names exist in your checkout before running them. Directory capitalization can also differ between repositories.

## Testing

The project documentation reports the following test results:

| Test Suite | Reported Result |
|---|---:|
| Backend Integration Tests | 77/77 passing |
| Flutter Automated Tests | 120/120 passing |
| Flutter Static Analysis | 0 issues |

Run the backend tests:

```bash
npm --prefix backend test
```

Run the Flutter tests:

```bash
cd CARE_BRIDGE
flutter test
```

Run Flutter static analysis:

```bash
flutter analyze
```

The documented test coverage includes authentication, role-based access control, ABHA demonstration workflows, hospital discovery, appointments, patient health records, accessibility, and multilingual rendering.

Test results may change as the project evolves. Run the tests locally to verify the current version.

## Project Structure

```text
CareBridge_System/
├── .env.example
├── package.json
├── README.md
├── scripts/
├── database/
│   ├── schema.sql
│   └── seed.sql
├── backend/
│   ├── package.json
│   ├── scripts/
│   ├── src/
│   │   ├── app.js
│   │   ├── server.js
│   │   ├── config/
│   │   ├── middleware/
│   │   ├── routes/
│   │   └── controllers/
│   └── test/
├── LOGIN/
├── ADMIN_DASHBOARD/
├── GOVERNMENT_DASHBOARD/
├── HOSPITAL_DASHBOARD/
└── CARE_BRIDGE/
    ├── pubspec.yaml
    ├── lib/
    └── test/
```

This is a high-level overview. Your local repository may contain additional files or use slightly different directory names.

## Security

CareBridge uses or is designed around the following security practices:

- JWT-based authentication.
- Password hashing using bcrypt.
- Server-side role-based authorization.
- Environment-based database configuration.
- Parameterized SQL queries.
- Controlled access to patient and administrative information.

Before deploying the application in a real healthcare environment, verify authorization across all endpoints, protect sensitive patient information, remove default demo credentials, configure production secrets, and complete the required security and regulatory reviews.

**ABDM/ABHA note:** Integration workflows in a project do not automatically establish official ABDM compliance or production approval. Verify the relevant integrations and requirements before making such claims.

## Maintainer and Project Partner

This project is developed collaboratively to explore digital public healthcare, hospital coordination, patient services, and healthcare information management.

### Maintainer — Mouleeshwaran S

- **GitHub Profile:** [@MOULEESHWARAN-S31](https://github.com/MOULEESHWARAN-S31)
- **Main Repository:** [CareBridge_System](https://github.com/MOULEESHWARAN-S31/CareBridge_System)

### Project Partner / Contributor — Monisha (Moni)

- **GitHub Profile:** [@Moni-sha24](https://github.com/Moni-sha24)
- **Repository:** [Care-Bridge](https://github.com/Moni-sha24/Care-Bridge)

Both contributors' profiles and repository links are provided to acknowledge their association with the CareBridge project.

## License

The project is intended to use the **MIT License**. Ensure that a valid `LICENSE` file is included in the repository before distributing the project under that license.
