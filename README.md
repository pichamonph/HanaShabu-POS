# Hana Shabu & Grilled - Restaurant Management System

A full-stack **Point of Sale (POS) and restaurant management system** built for Hana Shabu & Grilled, a Thai hotpot and grilled buffet restaurant. The system covers everything from customer reservations and table management to food ordering, inventory control, billing, and business analytics.

## Table of Contents

- [Features](#features)
- [Screenshots](#screenshots)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Database Schema](#database-schema)
- [API Routes](#api-routes)
- [Role-Based Access](#role-based-access)

## Features

### Customer-Facing
- **Online Reservation** - Book tables by date, time, and party size
- **Customer Registration & Login** - Account management with reservation history
- **QR Code Ordering** - Scan QR code at the table to browse the menu and place orders
- **Buffet Tier Selection** - Standard (229 THB) and Premium (339 THB) options
- **Promotions Display** - New member discounts, group rates, and couple packages

### Admin / Staff
- **Table Management** - Real-time table status across restaurant zones
- **Order Management** - Create, track, and update orders (Pending → Cooking → Served)
- **Menu Management** - Add/edit/delete menu items with images, categories, and dual-language names (TH/EN)
- **Inventory / Stock Control**
  - Track ingredient quantities with low-stock alerts
  - Stock import (purchasing) with supplier notes
  - Stock depletion (usage) logging
  - Batch operations and cancellation support
- **Billing & Payment** - Generate bills with VAT calculation, discounts, and payment method tracking
- **Employee Management** - Staff profiles, positions, and salary tracking
- **QR Code Generation** - Dynamic QR codes per order for customer scanning

### Super Admin / Management
- **Dashboard** - Total sales, costs, profit, and daily/weekly trends
- **Sales Analytics** - Revenue reports, top-selling products, category performance
- **Customer Insights** - Customer count, spending patterns, and table utilization
- **Staff Activity Tracking** - Monitor orders placed, bills opened per employee
- **Payment Method Summary** - Breakdown by payment type

## Screenshots

### Customer Pages
| Landing Page | Login | Reservation |
|:---:|:---:|:---:|
| ![Landing](sourceCode/public/hana_pos/main-menu-front.jpg) | ![Login](sourceCode/public/hana_pos/Login-frontend.jpg) | ![Reserve](sourceCode/public/hana_pos/reserve-chair.jpg) |

| Reservation History | QR Code Order |
|:---:|:---:|
| ![History](sourceCode/public/hana_pos/history-reserve-user.jpg) | ![QR Order](sourceCode/public/hana_pos/order-inQrcode.jpg) |

### Admin Pages
| Admin Login | Table Management | Today's Reservations |
|:---:|:---:|:---:|
| ![Admin Login](sourceCode/public/hana_pos/Login-backend.jpg) | ![Tables](sourceCode/public/hana_pos/Main-menu-manage-table.jpg) | ![Reservations](sourceCode/public/hana_pos/Today-Reservations.jpg) |

| Order by Table | Kitchen Orders | QR Code Order |
|:---:|:---:|:---:|
| ![Order Chair](sourceCode/public/hana_pos/order-chair.jpg) | ![Kitchen](sourceCode/public/hana_pos/list-order-in-kitchen.jpg) | ![QR Code](sourceCode/public/hana_pos/QRCode-order.jpg) |

| Order History | Payment | Receipt |
|:---:|:---:|:---:|
| ![Order History](sourceCode/public/hana_pos/order-history.jpg) | ![Payment](sourceCode/public/hana_pos/Payment.png) | ![Receipt](sourceCode/public/hana_pos/receipt.png) |

### Reservation Management
| Reservation List | Pending Detail | Confirmed Detail | Cancelled Detail |
|:---:|:---:|:---:|:---:|
| ![List](sourceCode/public/hana_pos/reserve-list-backend.jpg) | ![Pending](sourceCode/public/hana_pos/reserve-detail-wait.jpg) | ![Confirmed](sourceCode/public/hana_pos/reserve-detail-confirm.jpg) | ![Cancelled](sourceCode/public/hana_pos/reserve-detail-cancel.jpg) |

### Inventory Management
| Stock Overview | Add Ingredient | Edit Stock |
|:---:|:---:|:---:|
| ![Stock](sourceCode/public/hana_pos/stock-ingredian.jpg) | ![Add](sourceCode/public/hana_pos/new-ingredian.jpg) | ![Edit](sourceCode/public/hana_pos/edit-stock.jpg) |

| Import Ingredients | Import History | Withdrawal History | Stock Summary |
|:---:|:---:|:---:|:---:|
| ![Import](sourceCode/public/hana_pos/import-ingredian.jpg) | ![Import History](sourceCode/public/hana_pos/import-history.jpg) | ![Withdrawal](sourceCode/public/hana_pos/Product-Withdrawal-History.jpg) | ![Summary](sourceCode/public/hana_pos/summary-ingredian.jpg) |

### Employee & Dashboard
| Add Employee | Edit Employee | Admin Dashboard |
|:---:|:---:|:---:|
| ![Add](sourceCode/public/hana_pos/add-employee.jpg) | ![Edit](sourceCode/public/hana_pos/edit-employee-info.jpg) | ![Dashboard](sourceCode/public/hana_pos/admin-dashboard.jpg) |

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Framework** | Next.js 15 (App Router) |
| **Language** | TypeScript |
| **Frontend** | React 19, Tailwind CSS, shadcn/ui (Radix UI) |
| **Backend** | Next.js API Routes, Server Actions |
| **ORM** | Prisma 6 |
| **Database** | MySQL |
| **Auth** | Cookie-based session management, bcrypt |
| **Charts** | Recharts |
| **Forms** | React Hook Form + Zod |
| **QR Code** | qrcode.react |
| **Notifications** | Sonner |

## Project Structure

```
sourceCode/
├── prisma/
│   ├── schema.prisma          # Database schema
│   └── migrations/            # Database migrations
├── public/
│   ├── hana_pos/              # System screenshots
│   ├── images/                # Menu images
│   ├── user-images/           # UI assets (logo, backgrounds)
│   └── uploads/               # User-uploaded files
├── src/
│   ├── app/
│   │   ├── (auth)/            # Auth pages (login/register)
│   │   ├── (user)/            # Customer-facing pages
│   │   │   ├── landing/       # Home / landing page
│   │   │   ├── reservations/  # Reservation booking
│   │   │   └── order/         # Customer ordering
│   │   ├── admin/             # Admin panel
│   │   │   ├── tables/        # Table management
│   │   │   ├── order/         # Order management
│   │   │   ├── menu/          # Menu management
│   │   │   ├── stock/         # Inventory overview
│   │   │   ├── stockin/       # Stock imports
│   │   │   ├── stockout/      # Stock depletion
│   │   │   ├── users/         # Employee management
│   │   │   ├── que/           # Queue / reservations
│   │   │   └── qrcode/        # QR code generation
│   │   ├── superadmin/        # Super admin analytics
│   │   │   ├── dashboard/     # Business dashboard
│   │   │   ├── sales/         # Sales reports
│   │   │   └── staff/         # Staff management
│   │   ├── api/               # REST API endpoints
│   │   └── login/             # Admin login
│   ├── components/            # Reusable React components
│   │   ├── ui/                # shadcn/ui primitives
│   │   └── SuperAdmin/        # Dashboard components
│   ├── actions/               # Server actions
│   ├── utils/                 # Utilities (db client, types)
│   └── middleware.ts          # Auth middleware
├── package.json
├── tailwind.config.ts
└── tsconfig.json
```

## Getting Started

### Prerequisites

- **Node.js** v18 or higher
- **MySQL** database server
- **npm** or **yarn**

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/<your-username>/HanaShabu.git
   cd HanaShabu/sourceCode
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Configure environment variables**

   Create a `.env` file in the `sourceCode/` directory:

   ```env
   DATABASE_URL="mysql://username:password@localhost:3306/hanashabu"
   ```

4. **Set up the database**

   ```bash
   # Generate Prisma client
   npx prisma generate

   # Run database migrations
   npx prisma migrate deploy
   ```

5. **Start the development server**

   ```bash
   npm run dev
   ```

   Open [http://localhost:3000](http://localhost:3000) in your browser.

### Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |

## Database Schema

The system uses **MySQL** with **Prisma ORM**. Below is the entity-relationship overview:

```
Customer ──< Reservations >── Tables
                                │
Employee ──< Orders >───────── Tables
                │
                ├──< OrderItem >── MenuItems >── BuffetTypes
                │
                └─── Bill ─── Payment

Employee ──< Stock_In ──< Stock_In_Detail >── Stock
Employee ──< TimeScription >── Stock
```

### Key Models

| Model | Description |
|-------|-------------|
| `Customer` | Customer accounts with email-based authentication |
| `Tables` | Physical restaurant tables with type and status |
| `Reservations` | Table bookings with soft-delete support |
| `Orders` | Customer orders linked to tables, with unique QR code identifiers |
| `OrderItem` | Individual order items with status tracking (PENDING → COOKING → SERVED → CANCELLED) |
| `MenuItems` | Menu offerings with Thai/English names, images, and buffet type associations |
| `BuffetTypes` | Buffet tier definitions (Standard, Premium) with pricing |
| `Bill` | Invoices with VAT, discount, and payment status |
| `Payment` | Payment transactions with method type |
| `Stock` | Ingredient inventory with cost, quantity, and low-stock thresholds |
| `Stock_In` | Purchase/import records with cancellation support |
| `TimeScription` | Ingredient usage/depletion logs |

## API Routes

### Orders
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/orders` | List all orders |
| POST | `/api/orders/create` | Create a new order |
| GET | `/api/orders/get` | Get order details |
| POST | `/api/orders/submit-menu` | Submit menu items to an order |
| PUT | `/api/orders/update-status` | Update order item status |
| POST | `/api/orders/close` | Close an order |
| GET | `/api/orders/history` | Get order history |
| GET | `/api/orders/pending` | Get pending orders |
| GET | `/api/orders/notifications` | Get order notifications |

### Reservations
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/reservations` | List all reservations |
| GET | `/api/reservations/today` | Get today's reservations |
| PUT | `/api/reservations/:id` | Update reservation status |
| POST | `/api/user-reservations/create` | Create reservation (customer) |
| GET | `/api/user-reservations/getre` | Get customer reservations |
| POST | `/api/user-reservations/cancel` | Cancel a reservation |
| GET | `/api/user-reservations/check-tables` | Check available tables |

### Menu & Buffet
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET/POST | `/api/menuItems` | List or create menu items |
| PUT/DELETE | `/api/menuItems/:id` | Update or delete a menu item |
| GET | `/api/menuItems/category/:category` | Get items by category |
| GET | `/api/menuItems/buffetType/:id` | Get items by buffet type |
| GET | `/api/buffet` | List buffet types |

### Tables
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET/POST | `/api/tables` | List or create tables |
| PUT | `/api/tables/:id` | Update table status |

### Inventory
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET/POST | `/api/stock` | List or create stock items |
| PUT/DELETE | `/api/stock/:stockID` | Update or delete stock |
| GET/POST | `/api/stockin` | List or create stock imports |
| POST | `/api/stockin/cancel` | Cancel a stock import |
| GET/POST | `/api/stockout` | List or create stock depletion records |

### Billing & Payment
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/bills/create` | Create a bill |

### Employees
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET/POST | `/api/employees` | List or create employees |
| PUT/DELETE | `/api/employees/:id` | Update or delete employee |

### Analytics (Super Admin)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/superadmin/dashboard` | Dashboard overview |
| GET | `/api/superadmin/dashboard/summary` | Summary metrics |
| GET | `/api/superadmin/dashboard/orders` | Order analytics |
| GET | `/api/superadmin/dashboard/customers` | Customer analytics |
| GET | `/api/superadmin/dashboard/sales-by-time` | Sales by time period |
| GET | `/api/superadmin/dashboard/top-products` | Top-selling products |
| GET | `/api/superadmin/sales` | Sales reports |
| GET | `/api/superadmin/top-products` | Top products |
| GET | `/api/superadmin/products` | Product analytics |
| GET | `/api/superadmin/products/categories` | Category breakdown |
| GET | `/api/superadmin/payment-methods` | Payment method stats |
| GET | `/api/superadmin/customer/count` | Customer count |
| GET/POST | `/api/superadmin/staff` | Staff management |

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/login` | Staff/admin login |
| POST | `/api/register` | Customer registration |
| POST | `/api/customer` | Customer login |

## Role-Based Access

The system implements three access levels protected by middleware:

| Role | Access | Description |
|------|--------|-------------|
| **Super Admin** | `/superadmin/*` | Full access including analytics, sales reports, and staff management |
| **Admin** | `/admin/*` | Operational access: tables, orders, menu, inventory, billing, employees |
| **Customer** | `/(user)/*` | Reservations, menu browsing, QR code ordering |
