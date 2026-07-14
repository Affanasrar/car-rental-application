# 🚗 Car Rental Application

![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript)
![Prisma](https://img.shields.io/badge/Prisma-ORM-darkblue?style=for-the-badge&logo=prisma)
![Neon DB](https://img.shields.io/badge/Neon-Serverless_Postgres-green?style=for-the-badge&logo=neon)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-cyan?style=for-the-badge&logo=tailwind-css)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

A highly responsive, modern car rental management platform focused entirely on delivering a seamless UI/UX for browsing fleets and scheduling reservations. Built with the latest Next.js App Router and backed by a serverless PostgreSQL database.

---

## 📑 Table of Contents
1. [About the Project](#-about-the-project)
2. [Key Features & Design Philosophy](#-key-features--design-philosophy)
3. [Tech Stack](#-tech-stack)
4. [Database Architecture](#-database-architecture)
5. [Getting Started](#-getting-started)
6. [Detailed Folder Structure](#-detailed-folder-structure)
7. [Deployment](#-deployment)
8. [Roadmap](#-roadmap)
9. [License & Contact](#-license--contact)

---

## 📖 About the Project

This project was engineered to solve the complexity of typical rental applications by stripping away bloated features and focusing entirely on speed, accessibility, and straightforward reservation logic. 

**Note on Scope:** To maintain a strict focus on core UI/UX enhancements and frictionless booking:
- This application relies strictly on standard web interfaces (no PWA implementations).
- Zero mandatory user registration flows.
- No third-party API identity verification checks (e.g., Nadra).
- No integrated payment gateways (focuses purely on booking and reservation logging).

## ✨ Key Features & Design Philosophy

*   **⚡ Blazing Fast Browsing:** Server-Side Rendering (SSR) via Next.js ensures the vehicle catalog loads instantly.
*   **🎨 Pure UI/UX Focus:** Clean, distraction-free design built with Tailwind CSS.
*   **📅 Frictionless Booking Flow:** Users can select dates and book vehicles without logging in or verifying external accounts.
*   **🔒 Type-Safe Database Queries:** Full end-to-end type safety utilizing TypeScript and Prisma ORM.

---

## 💻 Tech Stack

**Frontend:**
*   [Next.js (App Router)](https://nextjs.org/) - React framework
*   [TypeScript](https://www.typescriptlang.org/) - Static typing
*   [Tailwind CSS](https://tailwindcss.com/) - Utility-first styling
*   Lucide React - Iconography

**Backend & Database:**
*   [Prisma](https://www.prisma.io/) - Next-generation ORM
*   [Neon DB](https://neon.tech/) - Serverless PostgreSQL database
*   Next.js Server Actions - For secure backend mutations

---

## 🗄️ Database Architecture

The application relies on a streamlined relational model. Below is a simplified look at the core Prisma schema:

```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model Car {
  id           String    @id @default(uuid())
  make         String
  model        String
  year         Int
  pricePerDay  Float
  isAvailable  Boolean   @default(true)
  imageUrl     String?
  bookings     Booking[]
  createdAt    DateTime  @default(now())
}

model Booking {
  id           String   @id @default(uuid())
  carId        String
  car          Car      @relation(fields: [carId], references: [id])
  customerName String
  contactInfo  String
  startDate    DateTime
  endDate      DateTime
  createdAt    DateTime @default(now())
}
🚀 Getting Started
Follow these steps to set up the project locally on your machine.

Prerequisites
Node.js: v18.17.0 or higher

Package Manager: npm (or yarn / pnpm)

Database: A free Neon PostgreSQL database URL.

Installation
Clone the repository

Bash
git clone [https://github.com/Affanasrar/car-rental-application.git](https://github.com/Affanasrar/car-rental-application.git)
cd car-rental-application
Install all dependencies

Bash
npm install
Set up Environment Variables
Create a .env file in the root directory and add your Neon connection string:

Code snippet
# .env
DATABASE_URL="postgres://[user]:[password]@[neon_hostname]/[dbname]?sslmode=require"
Initialize Prisma & Push Schema
Generate the Prisma Client and sync your schema with the Neon database:

Bash
npx prisma generate
npx prisma db push
Run the Development Server

Bash
npm run dev
Open http://localhost:3000 in your browser to view the application.

📁 Detailed Folder Structure
Plaintext
car-rental-application/
├── app/                        # Next.js App Router
│   ├── (routes)/               # Organized route groups (e.g., catalog, booking)
│   ├── api/                    # API endpoints (if needed alongside Server Actions)
│   ├── layout.tsx              # Root layout file
│   └── page.tsx                # Homepage / Landing page
├── components/                 # Reusable React components
│   ├── ui/                     # Base UI elements (buttons, inputs, cards)
│   └── shared/                 # Shared application components (Navbar, Footer)
├── lib/                        # Utility functions and configurations
│   ├── prisma.ts               # Prisma client instantiation
│   └── utils.ts                # Helper functions (e.g., date formatting, styling)
├── prisma/                     # Database schema and migrations
│   └── schema.prisma           # Main Prisma schema file
├── public/                     # Static assets (images, icons, fonts)
├── .env                        # Environment variables (ignored by git)
├── .gitignore                  # Git ignore rules
├── next.config.js              # Next.js configuration
├── tailwind.config.ts          # Tailwind CSS configuration
└── tsconfig.json               # TypeScript configuration
🌍 Deployment
This application is optimized for deployment on Vercel.

Push your code to your GitHub repository.

Go to Vercel and log in.

Click Add New Project and import your car-rental-application repository.

Add your DATABASE_URL in the Environment Variables section.

Click Deploy. Vercel will automatically detect Next.js and build your application.

🗺️ Roadmap
[ ] Advanced Filtering: Allow users to filter the car catalog by price range, make, and seating capacity.

[ ] Admin Dashboard: Create a protected /admin route to add/remove cars and view all incoming booking requests.

[ ] Pagination/Infinite Scroll: Optimize the car catalog for large fleets.

📜 License
This project is open-source and distributed under the MIT License.

👤 Author
Affan Ahmed

GitHub: @Affanasrar

If you found this project helpful, please consider giving it a ⭐ on GitHub!
