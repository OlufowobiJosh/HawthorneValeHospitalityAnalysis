# Data notes

## Included sources

[Hotel_Bookings_Data.xlsx](../data/Hotel_Bookings_Data.xlsx) is an unchanged copy of the supplied combined workbook. It contains the booking, room-rate and ancillary-service worksheets. The separately supplied room-rate and ancillary-service workbooks contain the same records as their corresponding sheets, so duplicate copies are not included.

| Worksheet | Source coverage |
| --- | --- |
| `hotel_bookings_data` | 7,665 populated source rows; 7,157 distinct booking identifiers |
| `room_rates` | 7 populated room-rate records |
| `ancillary_services` | 5,483 populated service records |

Blank formatted rows are excluded from these counts. Completed bookings have check-in dates across January–December 2025.

## Booking and category interpretation

- The booking sheet includes 508 repeated full rows. All repeated booking identifiers have identical supplied field values. The source workbook retains these rows; use distinct booking identifiers or an explicitly deduplicated table when counting bookings.
- Treating `Checked Out` and `Completed` as completed stays produces 6,867 distinct completed bookings. The remaining 290 distinct bookings are cancelled. These counts reconcile to the dashboard's booking-status chart.
- `OTA`, `O.T.A` and `Online Travel Agency` are source variants of the OTA channel label. Standardise these labels when comparing channel volumes.
- Some fields are blank for cancelled bookings. A blank discount is a source value, and its interpretation should follow the intended pricing calculation.
- Room-rate and ancillary-service records should be related at their stated keys. Check join grain before summing booking or revenue values.

## Dashboard and calculation scope

The JPG is the supplied static dashboard capture. Its month control changes the displayed monthly KPI comparison. Individual views should be interpreted using their own filters and measures.

The Tableau workbook, calculated fields, room-capacity assumptions and an interactive dashboard URL are not part of this repository. The source fields and booking counts can be reviewed independently, while exact reproduction of the revenue and capacity-based KPIs requires those Tableau definitions and assumptions.
