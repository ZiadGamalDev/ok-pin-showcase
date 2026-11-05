# OK-PIN technical notes

Scope: the REST API I wrote for the OKPIN mobile app (Laravel 10), delivered 2024. Everything below is visible in the API repo; items that were only plans are not listed.

## Structure
- `app/Http/Controllers/Auth`: Auth, Email, Phone (OTP by email or WhatsApp), Password, Pin, Fingerprint, Face, Profile.
- `app/Http/Controllers/Api`: Category, CategoryService, Voucher, VoucherService, Card (gift cards), Payment, Gateway, MerchantInfo, Ticket, TicketMessage, Notification, Report, Config.
- `app/Http/Services/OtpService.php`: one-time codes for email and WhatsApp verification.
- Auth by JWT; chat/notification events over Pusher; Stripe SDK for card payments.

## Purchase flows
- Top-up services and voucher cards each have normal-user and merchant prices; buying earns points; points can pay for a purchase.
- Voucher codes carry a serial and an expiry date. Gift cards are sold like cards but are activated by the client's team after purchase (client requirement, 2024-09-29).
- Payment methods: wallet, points and card (Stripe used for development; the client planned another gateway).

## Handover
- Postman collection of all endpoints sent to the client on 2024-12-04.
- API merged into the client's licensed dashboard script in December 2024.
