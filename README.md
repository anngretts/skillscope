# SkillScope

A test platform for learners, built as a 3-week team project during a 6-week software development bootcamp (ValiIT!). Admins and managers create new tests and new questions. Admins can create new levels and competences. Both admin and managers can assign test to the users, and users complete the tests assigned to them.

> **Status:** work in progress. Not all planned features are finished (see "Project status" below).

## Features

The platform has three user roles:

- **Admin**: creates tests and questions, links questions to levels and competencies, adds competencies and levels, invites users and managers, and can see all users of the platform.
- **Manager**: creates and assigns tests, creates questions, completes tests assigned to them, invites and manages users, creates groups and adds users to them.
- **User**: sees a dashboard and the tests assigned to them, and can complete them.

## Tech stack

- **Backend:** Java 21, Spring Boot 4.x, Gradle, PostgreSQL
- **Frontend:** Vue 3, Vite, Vue Router, Pinia, Axios, Bootstrap, JavaScript, HTML, CSS

## Project structure

```
backend/    Spring Boot REST API
frontend/   Vue 3 + Vite single-page app
docs/       Documentation and database scripts
```

## Getting started

### Requirements

- Java 21
- Node.js 20.19+ or 22.12+
- PostgreSQL (running locally)

### Database

PostgreSQL must be running on localhost with a database named `vali_it`:

```
jdbc:postgresql://localhost:5432/vali_it
```

Run the scripts from `docs/database` in this order:

1. `1_reset_database.sql`: drops and recreates the `testi_platvorm` schema
2. `2_create.sql`: creates all tables
3. `3_import.sql`: inserts the initial data

All tables live in the `testi_platvorm` schema. Connection settings (username, password) are in `backend/src/main/resources/application.properties`.

### Backend

```
cd backend
./gradlew bootRun
```

Other useful commands:
```
./gradlew build    # build the project
./gradlew test     # run tests
```

### Frontend

```
cd frontend
npm install
npm run dev
```

The app runs at http://localhost:8081.

## My contribution

Our team had 4 people and my part of the project was the following:

- Worked on the login view together with the team in the start of the project to get started. Created a POST request for /login. 
- Built the /tests view that shows all tests in the system. Only managers and admin can see this view. I fetched all test data from the backend with a GET API request and built a reusable card component where the test information is viewed. Other views use this component as well.
- Built the "My tests" view on /my-tests, which reuses the same components but shows only the tests assigned to the logged-in user (GET request tied to the user).
- Created the POST endpoint in the backend for creating questions in the question bank. Due to tight timeframe the frontend side of this feature, which at the moment sits in a modal was completed with AI assistance. 

## Project status

The core views and role structure are in place. Many planned functionality is not finished yet, because the project was built in three weeks but it is in progress.

Known limitations: user passwords in the sample data are stored as plain text, because password hashing (e.g. BCrypt with Spring Security) was not implemented within the project timeframe. The sample data is dummy data only. Do not use real passwords with this project.
