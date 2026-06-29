# Event Ticketing & Management System (API-Driven Platform)

A secure, multi-role Event Ticketing and Management platform. Built using **Laravel 11** as a headless RESTful API and **Vue 3 (Vite)** for a modern, decoupled, and highly responsive user interface.

---

## 🏗️ Project Architecture

The system utilizes a decoupled (Separation of Concerns) architecture:
* **Backend:** Laravel handling RESTful API endpoints, relational database indexing, business logic, multi-tier middleware security, PDF ticket generation, and custom QR Codes.
* **Frontend:** Vue 3 utilizing Composition API, Vue Router for client-side routing, and Axios to map asynchronous API network states.

---

## 🛠️ Tech Stack & Key Extensions

### Backend (Laravel Core)
* **Laravel Sanctum:** Stateful token-based API authentication.
* **SimpleSoftwareIO QrCode:** For unique electronic ticket encoding and physical event check-ins.
* **Barryvdh DomPDF:** Real-time runtime rendering of secure HTML payload into downloadable PDF tickets.

### Frontend (Vue.js Framework)
* **Vue 3 (Composition API)** + **Vite**
* **Vue Router & Axios Interceptors** ---

## 🔐 Multi-Role Authorization & Middleware Gates

The platform applies robust security constraints using a custom Role-based Middleware structure, dividing clients into 3 distinct layers:

### 1. Public Routes (Guest Level)
* **Authentication:** `POST /api/register` & `POST /api/login`
* **Discovery:** Browsing events, viewing single event details, and extracting dynamic ticket capacities.

### 2. Protected Routes (Authenticated via `auth:sanctum`)
* Global access to self-profile updates, credential mutations, and real-time Notification states (`/api/notifications`).

### 3. Role-Based Segments (`middleware: ["role:xxx"]`)
* **Attendee:** Can initialize event orders (`POST /orders`), track purchase history, view custom generated tickets, and initialize real-time PDF downloads.
* **Organizer:** Full CRUD lifecycle control over assigned events and dynamic ticket tier configurations (VIP, Standard, Early-Bird). Includes a verification system (`POST /validate`) to authorize and scan tickets at event gates.
* **Admin:** Full analytical overview via `admin/dashboard` with high-level access to approve or reject pending organizer events globally.

---

## 🚀 How to Set Up & Install

### Backend Setup
```bash
cd laravel-final-project
composer install
cp .env.example .env # Configure your database configurations here
php artisan key:generate
php artisan migrate --seed
php artisan serve

### frontend Setup

cd Event-Management-Ticketing-System/vue-app
npm install
npm run dev