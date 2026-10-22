# QueueLess — Smart Queue and Waiting-Time Management System

A beginner-friendly full-stack starter project using React, Java Spring Boot, and MySQL.

## Features included
- View available services
- Generate a digital token
- View queue position and estimated waiting time
- Admin controls: call next token and complete a token
- Basic queue statistics

> This is an educational starter project. It does not yet include user login, role-based security, SMS/email notifications, or production-grade concurrency protection.

## Requirements
- Java 21
- Maven 3.9+
- Node.js 20+
- MySQL 8+
- VS Code (or another editor)

## 1. Create the MySQL database
Open MySQL Workbench or a MySQL terminal and run:

```sql
CREATE DATABASE queueless;
```

## 2. Configure the backend
Open `backend/src/main/resources/application.properties`.
Change `spring.datasource.username` and `spring.datasource.password` to your local MySQL credentials.

## 3. Start the backend
In a terminal:

```bash
cd backend
mvn spring-boot:run
```

Backend URL: `http://localhost:8080`

The application creates its tables automatically and inserts sample services if the services table is empty.

## 4. Start the React frontend
Open a second terminal:

```bash
cd frontend
npm install
npm run dev
```

Open the URL printed by Vite, usually `http://localhost:5173`.

## API endpoints
- `GET /api/services` — list services
- `POST /api/tokens?serviceId=1&customerName=Harshada` — create token
- `GET /api/tokens` — list all tokens
- `GET /api/tokens/{id}` — get one token and queue position
- `POST /api/admin/call-next?serviceId=1` — call next waiting token
- `POST /api/admin/complete/{id}` — complete a token
- `GET /api/admin/stats` — basic queue statistics

## Important notes
- Token numbers are generated per service and are simple for a student demo.
- Waiting time is an estimate: number of waiting people ahead × average service minutes.
- The demo currently uses a simple customer name field instead of full authentication.
- Before real-world use, add Spring Security, authorization, validation, database transaction/locking for concurrent token requests, privacy controls, and tests.
