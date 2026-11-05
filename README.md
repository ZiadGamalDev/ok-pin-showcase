# OK-PIN: REST API for a digital-cards mobile app

Backend API I built (Laravel) for OKPIN, a mobile app for buying game top-ups, voucher codes and gift cards. Built in 2024 as part of a Dinamo team (Flutter app and admin dashboard by teammates), then handed over to the client's next developer.

## What I built
- Authentication: email and WhatsApp OTP, password reset, JWT, plus PIN, fingerprint and face login endpoints.
- Catalog and purchase flows for top-up services, voucher cards and gift cards, with voucher serials and expiry dates.
- Wallet and points payments, and a Stripe card payment used for testing until the client chose a gateway.
- Merchant (wholesale) pricing next to the normal user price.
- Support tickets with messages, push-style notifications over Pusher, search, reports, and app configuration endpoints (languages, countries, terms, privacy).
- A Postman collection documenting every endpoint, used by the client's next developer.

## Facts you can check
- Stack: Laravel 10 on PHP 8.1, JWT auth, Stripe, Pusher.
- Size of the API repo (measured 2024-12 code, counted 2026-11): 43 commits, about 5,400 lines of PHP in `app/`, 64 route definitions in `routes/api.php`, 4 feature test files for auth.
- The admin dashboard and storefront in the final product are a licensed CodeCanyon script (Gamers Arena by Bug-Finder) owned by the client; I merged my API into it in December 2024. Its source is not mine to share.

## Status
Delivered and handed over in December 2024. No public demo (the old demo domain is offline). The source is private and belongs to the client's project.

Contact: https://ziadgamal.com
