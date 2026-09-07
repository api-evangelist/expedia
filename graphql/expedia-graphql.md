---
generated: '2026-09-07'
method: probed
source: https://api.expediagroup.com/supply/lodging/graphql
---

# Expedia GraphQL

## THE PUBLISHED SURFACE (probed 2026-09-07)

Expedia Group operates a **real, first-party GraphQL API** for lodging connectivity partners:

| | |
|---|---|
| Endpoint | `https://api.expediagroup.com/supply/lodging/graphql` |
| Observed status | **HTTP 401**, empty body, on an anonymous POST |
| Introspection | **gated** — `{__schema{queryType{name}}}` returns 401 |
| Auth | OAuth 2.0 bearer token, per the Expedia Group connectivity documentation |
| Docs | https://connectivityportal.expediagroup.com/documentation/expedia (JavaScript-rendered; served as an HTML shell to a crawler) |
| Corroboration | Expedia Group publishes `com.expediagroup:expediagroup-sdk-graphql` (0.0.8-alpha, 2025-06-02) and `@expediagroup/lodging-connectivity-sdk` (0.0.2, 2024-09-29) — GraphQL clients for this surface |

A 401 on an anonymous POST is the correct, expected result for a partner API. **The endpoint exists and
the schema is real; we simply cannot read it without partner credentials, and we will not guess at it.**
The published SDL is therefore *not* in this repository, and no attempt has been made to reconstruct it
from documentation.

Other hosts probed and ruled out on 2026-09-07: `https://api.expediagroup.com/graphql` → 404
(`{"code":"NOT_FOUND"}`), `https://developers.expediagroup.com/openapi.json` → 404,
`https://developers.expediagroup.com/swagger.json` → 404, `https://apim.expedia.com/openapi.json` → 404.

## `expedia-schema.graphql` IS NOT EXPEDIA'S SCHEMA

> **Read this before using `graphql/expedia-schema.graphql` for anything.**
>
> That file is a **conceptual domain model written by API Evangelist**, not a document Expedia Group
> published and not the schema served at the endpoint above. It was authored in June 2026 by reading the
> Rapid/EPS REST documentation and modelling the travel domain in GraphQL syntax. It has never been
> validated against Expedia's live schema, because that schema is auth-gated (401).
>
> - Its type names, field names, nullability and arguments are **inferred**, not observed.
> - No query in it is known to execute against `api.expediagroup.com/supply/lodging/graphql`.
> - It must **never** be used to generate a client, to derive an error catalog, a data model, an
>   agentic-access contract, an MCP tool list, or an Agent Skill — deriving from it would propagate an
>   unverified model into artifacts that read as measured fact.
>
> It is retained only as a reading aid for the travel domain. `method: generated`,
> `x-generated-from: documentation`.

## Provider

- **Provider:** Expedia (a brand of Expedia Group)
- **Canonical catalog:** https://github.com/api-evangelist/expedia-group
- **Developer Portal:** https://developers.expediagroup.com/
- **GitHub:** https://github.com/ExpediaGroup

---

# Conceptual domain model (generated — see the warning above)

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
