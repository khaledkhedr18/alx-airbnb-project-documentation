# Airbnb Clone - Use Case Diagram Documentation

## Overview
This document describes the use case diagram for the Airbnb Clone backend system, visualizing interactions between key actors and system functionalities.

## Actors
1. **Guest** - User searching and booking properties
2. **Host** - User listing and managing properties
3. **Admin** - System administrator managing platform
4. **Payment System** - External payment processor

## Key Use Cases

### Guest Use Cases
- Register Account
- Login/Logout
- Search Properties
- Filter Listings
- View Property Details
- Book Property
- Make Payment
- Cancel Booking
- Write Review
- Manage Profile

### Host Use Cases
- Register as Host
- Create Listing
- Update Listing
- Delete Listing
- Manage Bookings
- Respond to Reviews
- Receive Payouts
- Set Availability

### Admin Use Cases
- Manage Users
- Moderate Listings
- View Reports
- Resolve Disputes
- Configure System

### System Use Cases
- Process Payments
- Send Notifications
- Validate Bookings
- Prevent Double Booking
- Calculate Pricing

## Use Case Relationships
- **Include** relationships:
  - "Book Property" includes "Make Payment"
  - "Create Listing" includes "Set Availability"

- **Extend** relationships:
  - "Cancel Booking" extends "Book Property"
  - "Write Review" extends "Book Property"

## Diagram Description
The use case diagram shows:
1. All actors on the left side
2. System boundary box containing all use cases
3. Connection lines showing which actors interact with which use cases
4. Relationships between use cases

## Special Scenarios
- **Payment Failure**: Extends "Make Payment" use case
- **Booking Conflict**: Extends "Book Property" use case
- **Content Flagging**: Extends "View Property Details" for reporting

## Technical Notes
- Diagram created using Draw.io
- Follows UML 2.0 standards
- Exported as PNG with transparent background
- Designed for both desktop and mobile viewing

Note: The actual PNG file with the diagram is included in the use-case-diagram/ directory of the repository. The diagram visually represents all the interactions described above with proper UML notation for actors, use cases, and relationships.
