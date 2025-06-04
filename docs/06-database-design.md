# 🗃️ Database Design

This section outlines the core relational schema for RiderX using PostgreSQL. It focuses on normalization, integrity, scalability, and extensibility.

---

## 🧑 User Table

```sql
Table: users
- id (UUID, PK)
- name (VARCHAR)
- phone (VARCHAR, UNIQUE)
- email (VARCHAR, UNIQUE)
- password_hash (TEXT) — optional if using OTP only
- role (ENUM: USER, DRIVER, ADMIN)
- referral_code (VARCHAR)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)
````

---

## 🚗 Driver Table

```sql
Table: drivers
- id (UUID, PK)
- user_id (FK → users.id)
- license_number (VARCHAR)
- vehicle_number (VARCHAR)
- vehicle_type (ENUM: BIKE, CAR)
- is_verified (BOOLEAN)
- is_online (BOOLEAN)
- average_rating (FLOAT)
- total_rides (INT)
```

---

## 🚘 Rides Table

```sql
Table: rides
- id (UUID, PK)
- rider_id (FK → users.id)
- driver_id (FK → drivers.id)
- pickup_lat (DECIMAL)
- pickup_lng (DECIMAL)
- drop_lat (DECIMAL)
- drop_lng (DECIMAL)
- status (ENUM: REQUESTED, ACCEPTED, STARTED, COMPLETED, CANCELLED)
- ride_type (ENUM: CAR, BIKE, CARPOOL)
- start_time (TIMESTAMP)
- end_time (TIMESTAMP)
- fare_amount (DECIMAL)
- payment_mode (ENUM: WALLET, UPI, CARD, CASH)
- rating (INT)
```

---

## 💳 Payments Table

```sql
Table: payments
- id (UUID, PK)
- ride_id (FK → rides.id)
- user_id (FK → users.id)
- amount (DECIMAL)
- status (ENUM: PENDING, COMPLETED, FAILED)
- transaction_ref (VARCHAR)
- provider (ENUM: RAZORPAY, STRIPE, CASHFREE, CASH)
- created_at (TIMESTAMP)
```

---

## 🔔 Notifications Table

```sql
Table: notifications
- id (UUID, PK)
- user_id (FK → users.id)
- title (TEXT)
- body (TEXT)
- type (ENUM: SMS, PUSH, EMAIL)
- status (ENUM: SENT, FAILED, PENDING)
- sent_at (TIMESTAMP)
```

---

## 🗺️ Location Cache (Redis Schema)

* `driver_location:{driver_id}` → (lat, lng, timestamp)
* `active_rides:{user_id}` → rideId + status
* `otp:{user_id}` → current OTP (TTL: 2 mins)

---

## Optional Tables (for future)

* `support_tickets`
* `promo_codes`
* `referrals`
* `ratings_and_reviews`

