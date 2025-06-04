# 🌐 API Design

This section describes the RESTful API endpoints for the RiderX platform. All endpoints follow REST conventions, return JSON responses, and are protected via JWT authentication unless noted.

Base URL (example): `https://api.riderx.in/v1`

---

## 🔐 Auth APIs

### POST `/auth/signup`
```json
{ "phone": "+919999999999" }
````

### POST `/auth/verify-otp`

```json
{ "phone": "+919999999999", "otp": "123456" }
```

### POST `/auth/login`

```json
{ "phone": "+919999999999", "otp": "123456" }
```

### POST `/auth/logout`

> Invalidates current token

---

## 👤 User APIs

### GET `/user/profile`

> Fetches logged-in user profile

### PUT `/user/profile`

```json
{ "name": "Aman", "email": "aman@example.com", "photo": "s3-url" }
```

### GET `/user/rides`

> List of past rides

---

## 🚘 Ride APIs

### POST `/rides/book`

```json
{
  "pickup": { "lat": 28.61, "lng": 77.23 },
  "drop": { "lat": 28.70, "lng": 77.10 },
  "type": "CAR"
}
```

### GET `/rides/estimate`

```json
{ "pickup": {...}, "drop": {...}, "type": "CAR" }
```

### GET `/rides/:id/status`

> Real-time ride status

### POST `/rides/:id/cancel`

> Rider cancels the ride

---

## 🚗 Driver APIs

### POST `/driver/go-online`

> Marks driver available

### POST `/driver/go-offline`

> Marks driver unavailable

### GET `/driver/ride-requests`

> Fetches nearby requests

### POST `/driver/accept-ride`

```json
{ "ride_id": "uuid" }
```

### POST `/driver/start-ride`

```json
{ "ride_id": "uuid", "otp": "1234" }
```

### POST `/driver/end-ride`

```json
{ "ride_id": "uuid" }
```

---

## 💳 Payment APIs

### POST `/payment/initiate`

```json
{ "ride_id": "uuid", "mode": "UPI" }
```

### GET `/payment/status/:ride_id`

> Status of payment transaction

---

## ⚙️ Admin APIs (secured with RBAC)

* `GET /admin/dashboard`
* `GET /admin/users`
* `GET /admin/rides`
* `PATCH /admin/resolve-dispute`
* `DELETE /admin/driver/:id`

---

## 🧪 Common Standards

* All API responses are wrapped:

```json
{
  "success": true,
  "data": {},
  "message": "Ride booked successfully"
}
```

* Standard HTTP status codes used
* Rate-limited via API gateway (e.g., AWS API Gateway / Nginx / Kong)

