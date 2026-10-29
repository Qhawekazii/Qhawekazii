# Airbnb Clone — a full-stack booking platform with a host dashboard

**Type:** Capstone project · **Solo**
**Code:** [github.com/Qhawekazii/Emily_AirbnbClone](https://github.com/Qhawekazii/Emily_AirbnbClone)
**Stack:** React + Vite · Node.js · Express 5 · MongoDB + Mongoose · JWT + bcrypt · Jest + Supertest · Heroku

---

## The problem

A booking platform has two sides that need different things from the same data. Guests browse listings and reserve dates; hosts create listings and see who has booked. The challenge was to build both sides on one API, with the right people allowed to do the right things.

## What I built

Three apps that share one backend:

| App | Who it's for | What it does |
|---|---|---|
| **REST API** | Both | Auth, listings, reservations, role checks |
| **Public site** | Guests | Home page, browse listings by location, listing details, reserve, "My reservations" |
| **Admin dashboard** | Hosts | Create, edit and delete listings; see reservations on their listings |

**Access control.** Passwords are hashed with bcrypt and every protected route checks a JWT. Hosts can only edit their own listings; listing all reservations is admin-only.

**Correct errors.** The API returns the right HTTP status codes (400, 401, 403, 404) instead of a generic 500, so the frontends can tell the user what actually went wrong.

**Tested.** 43 API tests across auth, listings, reservations and health checks, using Jest and Supertest.

**One-dyno deployment.** Express serves the API and both built React apps, so the whole platform deploys as a single Heroku app. I wrote a step-by-step deployment guide and full API docs.

## Problems I had to solve

- **Express 5 broke wildcard routes** used to serve the React apps — rewrote them for the new path syntax.
- **Mongoose 9 changed save hooks** — fixed the password-hashing and reservation hooks that silently stopped running.
- **Session restore on refresh** — reworked the auth context so a logged-in user stays logged in after reload, with clear login errors.

## What I'd improve

Add a root README with a live demo link, move the frontend API URL fully into environment config, and add date-overlap checks so two guests can't book the same nights.
