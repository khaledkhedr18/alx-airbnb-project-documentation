# 🧾 Backend Requirements Documentation

This document outlines the technical and functional requirements for three key backend features of the Airbnb Clone project.

---

## 1. 🔐 User Authentication

### Functional Requirements:

- Users can register as guests, hosts, or admins.
- Secure login using email and password.
- JWT-based session management.
- OAuth login via Google (optional).

### API Endpoints:

- `POST /api/v1/auth/register`
  **Description:** Register a new user.
  **Input:**

  ```json
  {
    "first_name": "John",
    "last_name": "Doe",
    "email": "john@example.com",
    "password": "secret123",
    "role": "guest"
  }
  ```

  **Output:**

  ```json
  {
    "token": "jwt_token_here",
    "user_id": "uuid"
  }
  ```

  **Validation:**

  - Email must be unique.
  - Password must be at least 8 characters.
  - Role must be one of: `guest`, `host`, `admin`.

- `POST /api/v1/auth/login`
  **Description:** Login existing user.
  **Input:**

  ```json
  {
    "email": "john@example.com",
    "password": "secret123"
  }
  ```

  **Output:** JWT token and user data.

### Performance Criteria:

- Token issued in < 1 second.
- Passwords hashed using bcrypt with minimum 10 rounds.

---

## 2. 🏠 Property Management

### Functional Requirements:

- Hosts can create, edit, and delete property listings.
- Each listing includes title, description, location, amenities, and price per night.
- Listings are searchable via location and filters.

### API Endpoints:

- `POST /api/v1/properties`
  **Description:** Add a new property (host only).
  **Input:**

  ```json
  {
    "name": "Cozy Apartment",
    "description": "Near the beach",
    "location": "Ismailia, Egypt",
    "price_per_night": 75.0
  }
  ```

  **Output:**

  ```json
  {
    "property_id": "uuid",
    "status": "created"
  }
  ```

- `PUT /api/v1/properties/:id` – Update a property.

- `DELETE /api/v1/properties/:id` – Delete a property.

- `GET /api/v1/properties?location=Cairo&min=50&max=100` – Search properties.

### Validation:

- Only users with `host` role can add/edit/delete.
- Price must be a positive number.

### Performance:

- Full-text search with indexing on `location` and `price`.

---

## 3. 📅 Booking System

### Functional Requirements:

- Guests can book a property for specific dates.
- No double bookings allowed (date validation).
- Booking status can be `pending`, `confirmed`, `cancelled`.

### API Endpoints:

- `POST /api/v1/bookings`
  **Description:** Book a property.
  **Input:**

  ```json
  {
    "property_id": "uuid",
    "start_date": "2025-07-01",
    "end_date": "2025-07-05"
  }
  ```

  **Output:**

  ```json
  {
    "booking_id": "uuid",
    "status": "pending"
  }
  ```

- `PATCH /api/v1/bookings/:id/cancel` – Cancel a booking.

### Validation:

- Check for existing bookings overlapping the requested dates.
- Ensure `start_date < end_date`.

### Performance:

- Response time under 1 second for booking creation.
- Use database constraints and indexed `start_date`, `end_date`.

---
