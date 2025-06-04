# 🔄 User Flows

This document outlines the key user flows in the RiderX platform for both Riders (Users) and Drivers.

---

## 👤 Rider (User) Flows

### 1. Signup & Login
- User enters mobile/email
- OTP verification (via Twilio/SMS)
- Create user profile (name, gender, photo, etc.)
- JWT token issued

### 2. Book a Ride
- User selects ride type (car/bike/carpool)
- Enters pickup and drop location
- Gets fare estimate and ETAs
- Confirms ride → sent to nearby drivers

### 3. Ride Experience
- Real-time driver tracking
- Driver arrives → OTP to start ride
- In-ride tracking and route display
- End ride → payment auto-initiated

### 4. Payments & Feedback
- Fare displayed with invoice breakdown
- Payment via wallet/UPI/card/cash
- User rates the driver (1–5 stars)
- Can report issue or request refund

---

## 🚗 Driver Flows

### 1. Onboarding
- Driver signs up with phone number
- Uploads documents: license, RC, insurance
- Admin verification (manual or automated)
- Profile approved → status: "Available"

### 2. Accept Ride
- Driver receives ride request (location + fare)
- Can accept/reject within 15 seconds
- Upon acceptance, GPS nav starts
- Ride begins after OTP validation

### 3. Ride Execution
- Navigate to destination
- End ride, collect fare (if needed)
- Earnings summary displayed

---

## 🛠 Admin/Support Flows

### 1. Dashboard Login
- Secure admin access (RBAC protected)
- Manage rides, users, drivers

### 2. Ride Monitoring
- Live ride map
- Can reassign/cancel/override rides if needed

### 3. Dispute Handling
- View and resolve complaints
- Initiate refunds or warnings

---

## 🔁 Other Flows

- Password reset via OTP/email
- Logout and token invalidation
- Notification preferences
- Referral and reward tracking
