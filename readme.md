# MP Subscription & Press System - Database Schema & Stored Procedures

## Project Description

This repository contains the **MySQL database schema** and **stored procedures** for a Member of Parliament (MP) management system. It handles:

- Subscription plans management (Basic, Pro, Premium, etc.)
- MP subscriptions with start/end dates and status tracking
- Press accounts and their export activity logs
- Analytical procedures for issue resolution, response times, promise delivery, and MP rankings

The design emphasizes data integrity (using InnoDB + Foreign Keys), performance (proper indexes), and consistency (UTC timestamps + utf8mb4).

## Database Tables

| Table Name              | Description |
|-------------------------|-----------|
| `SUBSCRIPTION_PLANS`    | Defines available subscription tiers with pricing and features (JSON) |
| `MP_SUBSCRIPTIONS`      | Records which plan each MP is subscribed to, including dates and status |
| `PRESS_ACCOUNTS`        | Press organizations and their contact details |
| `PRESS_EXPORTS`         | Logs all data exports performed by press accounts |

**Note**: Some stored procedures depend on additional tables created by other team members:
- `ISSUES`
- `ISSUE_UPDATES`
- `PROMISES`
- `MPs` (referenced as foreign key in `MP_SUBSCRIPTIONS`)

## Setup Instructions

### 1. Prerequisites
- MySQL 5.7 / 8.0+ (InnoDB supported)
- MySQL client, phpMyAdmin, or MySQL Workbench

### 2. Execution Steps

1. Open your MySQL client.
2. Run the following command first:
   ```sql
   SET SESSION time_zone = '+00:00';