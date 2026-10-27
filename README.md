# iMovies — Movie Ticket Booking System

iMovies is a full-stack web application for exploring movies and managing movie ticket bookings. Built around the MERN technology stack, the application brings together movie discovery, show selection, seat booking, booking management, reviews, favorites, and administrative tools.

The project is intended for local development and academic learning, using commonly available development tools and a MongoDB database.

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation and Setup](#installation-and-setup)
- [Environment Configuration](#environment-configuration)
- [Database Seeding](#database-seeding)
- [Admin Account Setup](#admin-account-setup)
- [API Reference](#api-reference)
- [Security and Data Integrity](#security-and-data-integrity)
- [Testing](#testing)
- [Demo Payment Disclaimer](#demo-payment-disclaimer)
- [Troubleshooting](#troubleshooting)
- [Future Enhancements](#future-enhancements)
- [License and Usage](#license-and-usage)

## Overview

The purpose of iMovies is to provide a convenient way for users to browse movies, check show information, select seats, and manage ticket bookings from a single application.

The administrative side supports the management of movie listings, theatres, shows, users, and booking information. The frontend communicates with the backend through APIs, while MongoDB stores the application's data.

### Project Highlights

- Movie catalogue with browsing and discovery features.
- User authentication and protected application areas.
- Movie, theatre, show, and booking management.
- Seat selection and availability management.
- Booking records and cancellation workflows.
- Administrative dashboard and management controls.
- Reviews and favorites functionality, where implemented.
- Simulated payment processing for demonstration purposes.

The exact availability of these features depends on the current implementation and configuration of the project.

## Key Features

### User Features

- **Account Management:** User registration, login, and logout.
- **Movie Catalogue:** Browse available movies and view their details.
- **Search and Filters:** Find movies using supported search criteria, genres, or languages.
- **Movie Information:** View available details such as ratings and trailer links.
- **Show Selection:** Explore show timings and theatre information.
- **Seat Selection:** Choose seats from the available seating layout.
- **Ticket Booking:** Submit a booking and receive its confirmation when successful.
- **Booking History:** Access previous and current bookings.
- **Cancellation:** Cancel eligible bookings according to the application's rules.
- **Favorites:** Maintain a personal list of preferred movies, if enabled.
- **Reviews:** Create and manage movie reviews, if enabled.
- **Demo Payments:** Test successful and unsuccessful payment scenarios without transferring real money.

### Administrative Features

- Dashboard for viewing booking-related information.
- Adding, editing, and removing movie records.
- Managing theatre information.
- Creating and updating movie shows.
- Reviewing booking information.
- Managing user and administrative access according to assigned roles.
- Monitoring booking statistics and simulated revenue, where supported.

### Reliability and Application Security

The application can use several measures to protect accounts and maintain consistent booking data:

- Password hashing using bcrypt.
- Authentication using JSON Web Tokens.
- Protected routes and role-based access control.
- Backend-side request validation.
- Server-side booking price calculations.
- Database constraints to prevent conflicting seat reservations.
- Centralized error handling.
- Authentication rate limiting, where configured.

These features should be checked against the actual source code before being described as fully implemented.

## Technology Stack

| Application Layer | Technology |
|---|---|
| Frontend | React.js, Vite, JavaScript |
| Backend | Node.js, Express.js |
| Database | MongoDB |
| Database Integration | Mongoose |
| Authentication | JWT and bcrypt |
| API Communication | HTTP and JSON |
| Package Management | npm |
| Version Control | Git and GitHub |
| Testing | Tools configured in the respective project packages |

MongoDB can be configured locally or through a compatible hosted database service. The database connection string must match the selected environment.

## System Architecture

The application follows a client-server model. The frontend provides the user interface, the Express backend processes requests and applies application rules, and MongoDB stores persistent information.

```text
┌──────────────────────────────────┐
│          React Frontend          │
│                                  │
│  Movie Catalogue                 │
│  Authentication                 │
│  Shows and Seat Selection        │
│  Bookings and User Dashboard     │
└────────────────┬─────────────────┘
                 │
                 │ HTTP / JSON / Cookies
                 ▼
┌──────────────────────────────────┐
│         Express Backend          │
│                                  │
│  API Routes and Controllers      │
│  Authentication and Validation   │
│  Movie and Theatre Management    │
│  Show and Booking Operations     │
│  Administrative Functionality    │
└────────────────┬─────────────────┘
                 │
                 │ Mongoose
                 ▼
┌──────────────────────────────────┐
│             MongoDB              │
│                                  │
│  Users and Movies                │
│  Theatres and Shows              │
│  Bookings and Payments           │
│  Reviews and Favorites           │
└──────────────────────────────────┘
```

### Architectural Components

**Frontend:** React renders the application pages and reusable components. Vite provides the development server and frontend build tooling.

**Backend:** Node.js and Express handle API requests, authentication, business logic, and communication with the database.

**Database:** MongoDB stores the application's records. Mongoose provides schemas, models, and database operations.

**Authentication:** The authentication system verifies user identity and controls access to protected features.

**Booking Workflow:** Booking requests are validated by the backend before the application updates booking and seat information.

**Administrative Access:** Administrative operations should be restricted to authorized accounts and verified by the backend, not just hidden in the frontend.

## Project Structure

The following is a representative structure for a React and Express application. Directory names should be adjusted to match the actual repository.

```text
IMovies/
├── client/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── context/
│   │   ├── hooks/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── utils/
│   │   └── styles.css
│   ├── .env.example
│   └── package.json
│
├── server/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── scripts/
│   ├── services/
│   ├── tests/
│   ├── utils/
│   ├── app.js
│   ├── index.js
│   ├── .env.example
│   └── package.json
│
├── .gitignore
└── README.md
```

### Main Directories

- `client/src/components/` — reusable interface components.
- `client/src/pages/` — application pages and screens.
- `client/src/context/` — shared application state, where used.
- `client/src/services/` — API communication and related services.
- `server/config/` — database and application configuration.
- `server/controllers/` — request handling and application logic.
- `server/models/` — database schemas and models.
- `server/routes/` — API endpoint definitions.
- `server/middleware/` — authentication, authorization, and request processing.
- `server/scripts/` — setup and database utility scripts.
- `server/tests/` — automated tests, if configured.

## Prerequisites

Install the required tools before starting the application.

- **Node.js:** Version supported by the project dependencies; Node.js 20 or 22 is a reasonable starting point for many current MERN projects.
- **npm:** Installed with Node.js.
- **MongoDB:** A local MongoDB installation or an accessible MongoDB deployment.
- **Git:** Useful for version control and repository management.
- **Code Editor:** Visual Studio Code or another compatible editor.

Check the installed versions:

```bash
node --version
npm --version
git --version
```

If MongoDB Shell (`mongosh`) is installed, check whether the database responds:

```bash
mongosh --eval "db.runCommand({ ping: 1 })"
```

A successful response indicates that the database is reachable. If the project uses a hosted database, configure its connection string instead.

## Installation and Setup

### 1. Open the Project

If the project is already downloaded, open the existing `IMovies` directory in your code editor.

If you are cloning your own repository, use its GitHub URL:

```bash
git clone https://github.com/milan05243/IMovies-Movie-Ticket-Booking.git
cd IMovies-Movie-Ticket-Booking
```

The folder name may differ depending on the directory created by Git.

### 2. Install Backend Dependencies

Open a terminal at the project root and navigate to the backend:

```bash
cd server
npm install
```

This installs the backend packages listed in `server/package.json`.

### 3. Configure the Backend Environment

If the project contains an `.env.example` file, create a local environment file.

**Windows PowerShell**

```powershell
Copy-Item .env.example .env
```

**macOS or Linux**

```bash
cp .env.example .env
```

Open `server/.env` and enter the configuration values required by the application. Never commit real credentials or secret keys to a public repository.

### 4. Install Frontend Dependencies

Open another terminal at the project root and run:

```bash
cd client
npm install
```

This installs the packages needed by the React frontend.

If the frontend uses an `.env.example` file, copy it to `.env` and configure the API URL according to the project's environment settings.

### 5. Start the Backend

From the `server` directory, run the development script defined in its `package.json`:

```bash
npm run dev
```

If the repository does not define a `dev` script, use the start command provided by the project. The expected backend address for this setup is:

`http://localhost:8000`

### 6. Start the Frontend

In the frontend terminal, run:

```bash
npm run dev
```

The expected Vite development address is:

`http://localhost:5173`

Open that address in your browser to access the application.

**Note:** Ports and startup commands depend on the repository's actual scripts and environment configuration. Update these instructions if your project uses different values.

## Environment Configuration

### Backend Environment Variables

The following table illustrates common backend settings. Use only variables supported by the actual backend code.

| Variable | Purpose | Example |
|---|---|---|
| `PORT` | Backend listening port | `8000` |
| `MONGO_URI` | MongoDB connection string | `mongodb://127.0.0.1:27017/Imovies` |
| `JWT_SECRET` | Secret used for signing authentication tokens | A securely generated random value |
| `CLIENT_URL` | Permitted frontend origin | `http://localhost:5173` |
| `NODE_ENV` | Application environment | `development` |

A local `.env` file may look like this:

```env
PORT=8000
MONGO_URI=mongodb://127.0.0.1:27017/Imovies
JWT_SECRET=replace_with_a_secure_random_secret
CLIENT_URL=http://localhost:5173
NODE_ENV=development
```

Use a different, securely generated secret for your own environment. Do not copy production secrets into the repository.

### Frontend Environment Variables

If the frontend reads its API address from a Vite environment variable, the file may contain:

```env
VITE_API_URL=http://localhost:8000/api
```

The exact variable name must match what the frontend source code reads. Some applications use a different variable or a fixed development URL.

## Database Seeding

Database seeding means inserting initial or sample records into the database so the application can be tested without manually entering every item.

If the repository includes a seed script, inspect `server/package.json` to find its exact command. A project might expose a script such as:

```bash
npm run seed
```

Do not run this command unless it is defined by the project. Check whether it creates, replaces, or deletes records before using it on a database containing important information.

## Admin Account Setup

Administrative access should be granted through the project's intended setup process.

If the repository provides an administrator creation script, inspect the available scripts and follow their documented instructions. Otherwise, use the supported account-management workflow and assign administrative privileges only through a trusted backend process.

Avoid putting default passwords, private credentials, or privileged account secrets into the README or source control.

## API Reference

The backend exposes HTTP endpoints through which the frontend communicates with application services.

The table below describes common endpoint patterns for a movie ticket booking system. Confirm the actual paths and methods in the project's route files before relying on them.

| Area | Example Endpoint | Purpose |
|---|---|---|
| Health | `GET /api/health` | Check backend availability, if implemented |
| Authentication | `POST /api/auth/register` | Register an account, if supported |
| Authentication | `POST /api/auth/login` | Sign in to an account |
| Authentication | `POST /api/auth/logout` | End the authenticated session |
| Movies | `GET /api/movies` | Retrieve movie listings |
| Movie Details | `GET /api/movies/:id` | Retrieve a movie record |
| Theatres | `GET /api/theatres` | Retrieve theatre listings |
| Shows | `GET /api/shows` | Retrieve show information |
| Bookings | `POST /api/bookings` | Submit a booking request |
| Booking History | `GET /api/bookings/my` | Retrieve the current user's bookings |
| Reviews | `/api/reviews` | Review-related operations, if implemented |
| Favorites | `/api/favorites` | Manage favorites, if implemented |
| Administration | `/api/admin/...` | Protected administrative operations, if implemented |

### Booking Request Example

A booking API may accept a JSON request containing a show identifier and selected seats. The following is an illustrative example, not a guarantee of the repository's exact request format:

```json
{
  "showId": "YOUR_SHOW_ID",
  "seats": ["A1", "A2"]
}
```

The backend should validate the show, verify seat availability, calculate the total price, and determine whether the booking can be completed. Never assume a booking succeeded unless the backend confirms it.

Protected endpoints should require authentication and the appropriate role.

## Security and Data Integrity

Security is an important part of an application that manages accounts, bookings, and personal information.

Recommended safeguards include:

- **Password Security:** Store password hashes rather than plaintext passwords.
- **Authentication:** Validate authentication tokens on protected requests.
- **Authorization:** Verify user roles on the backend before allowing administrative operations.
- **Input Validation:** Check incoming data before processing database operations.
- **Seat Availability:** Prevent conflicting reservations for the same seat and show.
- **Price Verification:** Calculate booking totals on the server instead of trusting prices sent by the browser.
- **Error Handling:** Return appropriate error responses without exposing sensitive internal details.
- **Secret Management:** Keep database credentials and authentication secrets out of committed files.
- **Request Protection:** Apply suitable rate limits to sensitive endpoints.

These are design and implementation considerations, not a substitute for testing or a formal security audit. Actual protection depends on the code, configuration, and database constraints in place.

## Testing

Testing helps verify that the application's main workflows work as expected and that errors are handled correctly.

First, inspect the scripts in `server/package.json` and `client/package.json` to identify the test commands supported by the repository.

For example, if the backend defines a test script, run:

```bash
cd server
npm test
```

If the frontend also defines a test script, run:

```bash
cd client
npm test
```

To check the frontend production build, if the corresponding script exists:

```bash
npm run build
```

### Suggested Test Areas

- User registration and login.
- Authentication and protected routes.
- Administrative access restrictions.
- Movie and show information.
- Theatre management.
- Seat availability and booking creation.
- Duplicate-seat booking attempts.
- Booking cancellation.
- Payment simulation and failure handling.
- Favorites and reviews, if implemented.
- Database connection failures.
- Frontend navigation and responsive layout.

Record the tests that actually run and their results. Do not describe an unexecuted test as passed.

## Demo Payment Disclaimer

If the project uses simulated payments, all payment results are intended for demonstration and testing only.

**A simulated payment is not a real financial transaction.** It does not transfer money or confirm that an external payment provider has processed a charge. Any displayed booking revenue or refund status must be interpreted according to the application's simulation logic.

If a real payment gateway is added in the future, it must be configured and tested separately using the provider's supported integration and security requirements.

## Troubleshooting

| Problem | Possible Solution |
|---|---|
| `npm` is not recognized | Install Node.js and reopen the terminal. |
| Dependencies fail to install | Check the Node.js version and the package's dependency requirements. |
| MongoDB connection fails | Verify that MongoDB is running and check `MONGO_URI`. |
| Backend does not start | Review the backend terminal output and verify its scripts and environment variables. |
| Frontend cannot connect to the API | Confirm the backend is running and check the configured API URL. |
| CORS errors appear | Ensure the backend permits the frontend's configured origin. |
| Authentication fails | Check the login response, token or cookie configuration, and backend logs. |
| A booking cannot be completed | Refresh the show information and verify seat availability. |
| A port is already in use | Stop the process using the port or configure another available port. |
| Test commands are unavailable | Inspect the scripts defined in the relevant `package.json`. |

## Future Enhancements

Possible improvements for future versions include:

- Integration with a legitimate payment provider.
- Email-based booking confirmations.
- Better mobile responsiveness and accessibility.
- Personalized movie recommendations.
- Improved booking and seat-availability analytics.
- Additional automated tests.
- Production deployment with appropriate security configuration.
- Better logging and application monitoring.

These are potential extensions and should not be treated as existing functionality until they have been implemented and tested.

## License and Usage

Before redistributing or publishing code from an existing project, review the applicable license and permission requirements. The absence of a license does not automatically grant permission to reuse or redistribute code.

For an academic project, document your own modifications, test results, and additional functionality accurately. Retain any third-party notices required by the applicable terms.

## Developer

**Milan Choudhary**  
B.Tech — Computer Science and Engineering (AI)  
Medicaps University

GitHub: (https://github.com/milan05243/IMovies-Movie-Ticket-Booking)

