# Data dictionary

The workbook [Hotel_Bookings_Data.xlsx](../data/Hotel_Bookings_Data.xlsx) contains the three source worksheets below. This dictionary describes the supplied fields; it does not assert database constraints or reproduce Tableau calculated fields.

## `hotel_bookings_data`

| Column | Description |
| --- | --- |
| `Booking ID` | Identifier linking a booking to ancillary-service records |
| `Booking Date` | Date the reservation was made |
| `Check-in Date` | Recorded arrival date |
| `Check-out Date` | Recorded departure date; missing for cancelled bookings in the supplied data |
| `Room Type` | Broad room category: Standard, Deluxe or Suite |
| `Room Type ID` | Identifier linking the booking to the room-rate table |
| `Seasonal Adjustment` | Source seasonal code: B, M or P |
| `Discount` | Source discount value, where populated; the supplied values are 5 and 10 |
| `Booking Channel` | Source booking channel; includes Direct, Online and several OTA labels |
| `Number of Rooms Booked` | Number of rooms on the booking record |
| `Guest Type` | Guest segment: Corporate or Leisure |
| `Loyalty Member` | Boolean loyalty-membership indicator, where populated |
| `Booking Status` | Source status: Checked Out, Completed or Cancelled |

The discount field has no explicit unit in its header. Its treatment in a revenue calculation should follow the original project definition.

## `room_rates`

| Column | Description |
| --- | --- |
| `Room Type ID` | Room-category identifier used to match bookings to rate information |
| `Room Sub-Type` | Room description: Standard Single, Standard Double, Deluxe A, Deluxe Garden View, Deluxe Balcony, Junior Suite or Luxury Suite |
| `Base Rate` | Base room-rate value |
| `Peak Season Adjustment Factor` | Peak-season multiplier; supplied value is 1.25 |
| `Moderate Season Adjustment Factor` | Moderate-season multiplier; supplied value is 1.10 |

## `ancillary_services`

| Column | Description |
| --- | --- |
| `Booking ID` | Booking identifier associated with the service record |
| `Ancillary Service Type` | Service category: Dining, Spa or Event |
| `Service Revenue` | Recorded service-revenue value |

## Relationships

| Booking-table field | Related field | Purpose |
| --- | --- | --- |
| `Room Type ID` | `room_rates.Room Type ID` | Associate bookings with room descriptions and rate inputs |
| `Booking ID` | `ancillary_services.Booking ID` | Associate bookings with recorded ancillary services |

Not every booking has a service record. Preserve bookings without ancillary services when analysing total booking volumes. See [data notes](DATA_NOTES.md) for repeated booking records and status/category variants.
