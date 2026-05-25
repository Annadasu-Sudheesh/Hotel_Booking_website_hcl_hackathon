# Hotel Booking Demo

LuxeStay is a full-stack hotel booking demo built with:

- `frontend/`: React + Vite
- `backend/`: Spring Boot + Spring Security + JPA
- `database`: seeded H2 in-memory database by default

The project now starts with mock hotel inventory, sample rooms, amenities, bookings, customer users, and a seeded admin account so the app is ready for demos immediately.

## Features

- Browse a polished hotel catalog
- Open hotel detail pages and inspect room inventory
- Book rooms through a live backend flow
- View and cancel bookings from the profile page
- Sign in as admin and review seeded inventory, users, revenue, and bookings
- Access H2 console for inspection during development



## Project Structure

```text
New folder/
|- backend/
|  |- src/main/java/com/example/backend/
|  |  |- config/
|  |  |- controller/
|  |  |- dto/
|  |  |- model/
|  |  |- repository/
|  |  |- service/
|  |- src/main/resources/application.properties
|  |- pom.xml
|- frontend/
|  |- src/
|  |  |- context/
|  |  |- pages/
|  |  |- services/
|  |  |- App.jsx
|  |  |- index.css
|  |- package.json
|- README.md
```

## Backend Setup

### Requirements

- Java 17+
- Maven 3.9+

### Run the backend

```bash
cd backend
mvn spring-boot:run
```

By default the backend starts on:

- `http://localhost:8080`

### Default database configuration

The backend uses H2 in-memory mode by default:

```properties
spring.datasource.url=jdbc:h2:mem:hotel_booking;MODE=MySQL;DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE
spring.datasource.username=sa
spring.datasource.password=
spring.datasource.driver-class-name=org.h2.Driver
```

You can override this with environment variables:

- `SPRING_DATASOURCE_URL`
- `SPRING_DATASOURCE_USERNAME`
- `SPRING_DATASOURCE_PASSWORD`
- `SPRING_DATASOURCE_DRIVER_CLASS_NAME`

### H2 Console

Open:

- `http://localhost:8080/h2-console`

Use:

- JDBC URL: `jdbc:h2:mem:hotel_booking`
- Username: `sa`
- Password: leave blank

## Frontend Setup

### Requirements

- Node.js 18+
- npm

### Install dependencies

```bash
cd frontend
npm install
```

### Run the frontend

```bash
npm run dev
```

The frontend runs by default on:

- `http://localhost:5173`

### API base URL

The frontend uses:

- `VITE_API_URL`

If not provided, it falls back to:

- `http://localhost:8080/api`

## Build and Test

### Frontend production build

```bash
cd frontend
npm run build
```

### Backend tests

```bash
cd backend
mvn test
```

## Main Routes

### Frontend

- `/` home
- `/hotels` hotel catalog
- `/hotels/:id` hotel detail
- `/checkout?roomId=...` booking flow
- `/profile` customer booking history
- `/login` sign in, register, password reset
- `/admin` admin dashboard

### Backend API

- `/api/auth/login`
- `/api/auth/register`
- `/api/auth/forgot-password`
- `/api/hotels`
- `/api/rooms`
- `/api/bookings`
- `/api/admin/dashboard`
- `/api/admin/bookings`
- `/api/admin/users`

## Notes

- Hotel and room browsing is public.
- Booking and profile actions require authentication.
- The admin dashboard expects the seeded admin account.
- The backend is currently optimized for local development and demo use.


## Current Development Defaults

- Backend port: `8080`
- Frontend port: `5173`
- H2 console enabled: `true`
- JWT auth enabled
- Seed data enabled automatically when the database is empty
