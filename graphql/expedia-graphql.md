# Expedia GraphQL Schema

## Overview

Expedia is one of the world's leading travel platforms, operating a portfolio of brands including Expedia, Hotels.com, Vrbo, Orbitz, Travelocity, Hotwire, Wotif, and trivago. The Expedia Group developer platform exposes travel inventory and booking capabilities through the RAPID API and other REST/SOAP interfaces. This conceptual GraphQL schema represents the core domain model underlying Expedia's travel booking capabilities.

## Schema Source

- **Provider:** Expedia / Expedia Group
- **Developer Portal:** https://developers.expediagroup.com/
- **GitHub:** https://github.com/ExpediaGroup
- **Schema Type:** Conceptual (derived from REST/RAPID API surface)
- **Schema File:** expedia-schema.graphql

## Domain Coverage

The schema covers the following travel booking domains:

### Properties and Lodging
Types covering hotels, vacation rentals, and other accommodation: `Property`, `Hotel`, `Room`, `RoomType`, `RatePlan`, `Rate`, `Price`, `Tax`, `Fee`, `Amenity`, `Media`.

### Availability and Search
Types supporting inventory search and availability checks: `Availability`, `AvailabilityRange`, `SearchResult`, `PropertySearch`, `SearchCriteria`.

### Bookings and Reservations
Types covering the end-to-end reservation lifecycle: `Booking`, `Reservation`, `RoomReservation`, `CancellationPolicy`, `CancellationPenalty`, `Voucher`.

### Guests and Payments
Types representing traveler and payment information: `Guest`, `GuestContact`, `Payment`, `BillingInfo`.

### Flights and Air Travel
Types for flight search, booking, and seat management: `Flight`, `AirRoute`, `Airline`, `Seat`, `SeatMap`, `FlightBooking`, `Itinerary`, `ItineraryItem`.

### Car Rentals
Types supporting car rental search and booking: `CarRental`, `CarType`, `RentalLocation`, `Vendor`.

### Activities and Experiences
Types for tours, activities, and destination content: `Activity`, `Tour`, `Destination`, `Point`, `PointOfInterest`.

### Reviews and Content
Types for user-generated content and media: `Review`, `ReviewSummary`.

### Financial and Currency
Types for monetary amounts and currency handling: `Currency`, `Money`, `Insurance`, `TravelInsurance`.

### Loyalty and Offers
Types supporting loyalty programs, deals, and special offers: `LoyaltyProgram`, `LoyaltyAccount`, `LoyaltyPoints`, `TravelPackage`, `VacationPackage`, `Offer`, `Deal`.

### API Access
Types for API credential management: `APICredential`, `RapidKey`.

## Key Queries

- `searchProperties` — Search hotels and vacation rentals by location, dates, and guest count
- `getProperty` — Retrieve detailed property information including rooms and rates
- `checkAvailability` — Check room availability for specific dates
- `searchFlights` — Search available flights between origins and destinations
- `getBooking` — Retrieve booking details by confirmation number
- `getItinerary` — Retrieve a full trip itinerary
- `searchActivities` — Search tours and activities at a destination
- `getLoyaltyAccount` — Retrieve loyalty program account and points balance

## Key Mutations

- `createBooking` — Create a new hotel or package booking
- `cancelBooking` — Cancel an existing booking
- `createFlightBooking` — Book a flight itinerary
- `addPayment` — Add payment information to a booking
- `redeemLoyaltyPoints` — Apply loyalty points to a booking

## References

- Expedia Group Developer Portal: https://developers.expediagroup.com/
- RAPID API Documentation: https://developers.expediagroup.com/docs/rapid
- ExpediaGroup GitHub: https://github.com/ExpediaGroup
