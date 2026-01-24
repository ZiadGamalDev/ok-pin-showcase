# OK-PIN Project Documentation

## Executive Summary
OK-PIN is a comprehensive digital marketplace platform built with Laravel that facilitates the trading of digital assets and services. The platform connects people who want to buy digital products with those who are selling them, handling everything from browsing and comparing options to secure payment processing and digital delivery.

## Project Overview
**Industry**: E-commerce / Digital Marketplace
**Role**: Lead Backend Developer
**Status**: Production-Ready
**Year**: 2026

OK-PIN allows users to:
- **Buy game vouchers** for popular games like Fortnite, PUBG, or Roblox.
- **Purchase gift cards** for platforms like Steam, PlayStation, or Amazon.
- **Top up gaming accounts** directly with credits or currency.
- **Sell your own digital products** to other users through the marketplace.
- **Manage a digital wallet** for storing funds and processing payments.

## Core Features

### Digital Products Management
- **Top-Up Services**: Game recharge and credits top-up with dynamic form generation (Player ID vs Zone ID).
- **Game Vouchers**: Digital game voucher management with serial codes, atomic locking for concurrency, and real-time inventory tracking.
- **Gift Cards**: Digital gift card management with unique codes, multiple tiers, and discount systems.

### User-to-User Marketplace (Sell Posts)
- Users can create posts to sell digital products.
- Escrow-like mechanism: funds held until delivery confirmation.
- State Machine: `Pending` -> `Negotiating` -> `Paid` -> `Delivered` -> `Completed`.
- Chat functionality between buyers and sellers.

### User Management
- **Authentication**: Multiple verification methods, social login.
- **KYC Verification**: Identity verification (Driving License, Passport, ID) with admin approval flow.
- **Wallet System**: Balance management, deposits via multiple gateways, withdrawals, and transaction history.

### Administrative Controls
- **Dashboard**: System statistics, user growth, transaction volume.
- **Product Management**: Code management, bulk import, category management.
- **Content Management**: Multi-language CMS (RTL/LTR), theme customization.
- **Financial Management**: Transaction monitoring, payment approval, withdrawal processing.

## Technical Architecture

### Stack
- **Backend**: Laravel 10 (PHP 8.2)
- **Frontend**: Blade Templates, jQuery, Bootstrap
- **Database**: MySQL, Redis
- **Infrastructure**: Apache/Nginx

### Database Design
The database includes:
- **User Management**: `users`, `admins`, `kycs`.
- **Products**: `categories`, `vouchers`, `gift_cards`, `voucher_codes`.
- **Transactions**: `funds`, `transactions`, `gateways`, `payout_logs`.
- **Content**: `contents`, `templates`, `languages`.
- **Support**: `tickets`, `ticket_messages`.

### Key Challenges & Solutions
1.  **Concurrency in Purchasing**:
    *   *Problem*: High demand led to race conditions (double spending of codes).
    *   *Solution*: Implemented pessimistic database locking ("Select for Update") during checkout.
2.  **Dynamic Pricing**:
    *   *Problem*: Complex tier-based pricing and temporary discounts.
    *   *Solution*: `PriceCalculator` service layering base price, user markup, and promotion rules.

## Monetization Model
1.  Transaction fees on purchases.
2.  Commission on user-to-user sales.
3.  Markup on digital product prices.
4.  Featured listing fees.
5.  Premium membership options.
