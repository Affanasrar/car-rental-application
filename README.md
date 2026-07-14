# Car Rental Application

![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript)
![Prisma](https://img.shields.io/badge/Prisma-ORM-darkblue?style=for-the-badge&logo=prisma)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-4169E1?style=for-the-badge&logo=postgresql)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.3-38B2AC?style=for-the-badge&logo=tailwind-css)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

An app-router based car rental experience for browsing car classes, signing in with Google, creating reservations, and managing existing bookings. The project uses Next.js, Prisma, NextAuth, and a PostgreSQL database with a polished UI built from Tailwind CSS and shadcn/ui components.

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Tech Stack](#tech-stack)
4. [Project Structure](#project-structure)
5. [Database Model](#database-model)
6. [Environment Variables](#environment-variables)
7. [Getting Started](#getting-started)
8. [Available Scripts](#available-scripts)
9. [Deployment](#deployment)
10. [License](#license)

## Overview

The application is centered around a simple booking flow:

1. Browse available car classes and locations on the home page.
2. Sign in with Google when you are ready to reserve.
3. Choose pickup location, pickup and return dates, car class, and whether the renter is under 25.
4. Review the pricing summary and confirm the reservation.
5. View and cancel reservations from the reservations page.

The UI is built as a responsive web app and is designed to keep the booking journey straightforward rather than overloaded with extra steps.

## Features

- Home page with a reservation form and a fleet overview.
- Car class detail pages with descriptions, features, and example vehicles.
- Google authentication through NextAuth.
- Reservation creation with date validation and pricing summary.
- Reservations dashboard for signed-in users.
- Reservation cancellation flow with confirmation dialog.
- Prisma-backed data access for classes, locations, users, and reservations.
- Reusable UI primitives sourced from shadcn/ui and Radix components.

## Tech Stack

- Next.js 14 with the App Router
- React 18
- TypeScript
- Tailwind CSS
- shadcn/ui and Radix UI
- Prisma ORM
- PostgreSQL
- NextAuth with Google provider
- Zod and react-hook-form for reservation validation
- date-fns for date formatting and calculations

## Project Structure

```text
src/
  app/
    api/auth/[...nextauth]/route.ts   NextAuth route
    cars/[id]/page.tsx                Car class detail page
    reservations/page.tsx             Signed-in user reservations
    layout.tsx                        Root layout and providers
    page.tsx                          Home page
  components/                         Shared UI and feature components
    ui/                               Base design system components
  helpers/                            Reservation helpers
  lib/                                Auth, data access, actions, Prisma, utilities
prisma/
  schema.prisma                       Database schema
  seed.ts                             Seed script
public/                               Static assets
```

## Database Model

The Prisma schema is built around the following core entities:

- User, Account, and Session for NextAuth.
- Class for car categories and example vehicles.
- Location for pickup locations.
- Reservation for booked rentals.

Reservations store pickup and return dates, the selected class, the selected location, the young-renter flag, the total price, and the user that created the booking.

## Environment Variables

Create a .env file in the project root with the following values:

```bash
DATABASE_URL="postgresql://USER:PASSWORD@HOST:PORT/DATABASE?sslmode=require"
DATABASE_URL_NON_POOLING="postgresql://USER:PASSWORD@HOST:PORT/DATABASE?sslmode=require"
GOOGLE_CLIENT_ID="your-google-oauth-client-id"
GOOGLE_CLIENT_SECRET="your-google-oauth-client-secret"
```

If your deployment platform provides a separate non-pooled connection string, use it for DATABASE_URL_NON_POOLING as well.

## Getting Started

### Prerequisites

- Node.js 18 or newer
- npm
- A PostgreSQL database
- Google OAuth credentials for NextAuth

### Install

```bash
git clone https://github.com/Affanasrar/car-rental-application.git
cd car-rental-application
npm install
```

### Set up the database

```bash
npx prisma generate
npx prisma db push
```

If you want to load seed data, run:

```bash
npm run db:seed
```

### Run locally

```bash
npm run dev
```

Then open http://localhost:3000.

## Available Scripts

- npm run dev: start the development server
- npm run build: create a production build
- npm run start: run the production server
- npm run lint: run ESLint
- npm run studio: open Prisma Studio
- npm run migrate:dev: create and apply a local Prisma migration
- npm run migrate:deploy: apply Prisma migrations in production
- npm run db:seed: seed the database

## Deployment

This project is ready for deployment on Vercel.

1. Push the repository to GitHub.
2. Import the repository into Vercel.
3. Add DATABASE_URL, DATABASE_URL_NON_POOLING, GOOGLE_CLIENT_ID, and GOOGLE_CLIENT_SECRET in the environment settings.
4. Deploy the project.

Vercel will detect the Next.js app automatically.

## License

This project is licensed under the MIT License.

## Author

Affan Ahmed

GitHub: @Affanasrar
