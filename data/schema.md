# Data schema

This file records the meanings of fields used in the travel-planning CSV datasets.

## `destination_ecosystems_phase2_complete_207.csv`

This dataset maps London-accessible destination airports to a draft long-weekend destination ecosystem.

| Field | Meaning | Notes |
|---|---|---|
| `airport_iata` | Three-letter IATA code for the destination airport. | Stable airport identifier. |
| `airport_name` | Human-readable airport name. | May be simplified rather than the airport's full official legal name. |
| `country` | Country or territory where the airport is located. | Used for filtering and grouping. |
| `london_routes` | Known London airport and airline route information. | Currently incomplete/blank in many rows; intended for later enrichment with routes such as `LGW easyJet`, `STN Ryanair`, etc. |
| `destination_ecosystem` | The best long-weekend destination ecosystem associated with the airport. | This is the wider visitor area or experience cluster, not necessarily the airport city itself. Examples: `Bay of Kotor`, `Ghent–Bruges–Brussels`, `Naples–Pompeii–Amalfi`. |
| `ecosystem_status` | Confidence/status flag for the ecosystem mapping. | Current values include `draft_assigned` and `needs_research`. |

## Planned next-phase fields

These fields are not yet in the CSV, but are intended for the travel-friction/access phase.

| Field | Meaning | Notes |
|---|---|---|
| `anchor_place` | The specific main place used for measuring access from the airport. | Example: for `Bay of Kotor`, the anchor might be `Kotor`; for `Eastern Algarve`, it might be `Tavira`. |
| `transfer_time_min` | Estimated travel time from the airport to the anchor place, in minutes. | Later used for scoring the <45 minute preference. |
| `transfer_mode` | Main mode or combination of modes from airport to anchor place. | Examples: `taxi`, `train`, `bus`, `ferry`, `train + taxi`. |
| `transfer_complexity` | Qualitative friction of the transfer. | Suggested values: `simple`, `moderate`, `difficult`. |
| `distance_score` | Score for airport-to-anchor convenience. | Suggested 1–10 score, with destinations above 45 minutes scoring lower. |

## Concept definitions

### Destination ecosystem

The broader visitor area or experience cluster associated with an airport. It may be a city, coastal region, island, historic area, scenic region, or cluster of nearby attractions.

### Anchor place

The concrete town/city/place within a destination ecosystem used to measure transfer time and travel friction. This is usually where a visitor would stay or travel to first.

Example:

| Airport | Destination ecosystem | Anchor place |
|---|---|---|
| `TIV` | Bay of Kotor | Kotor or Perast |
| `FAO` | Eastern Algarve–Tavira–Ria Formosa | Tavira |
| `BRU` | Ghent–Bruges–Brussels | Ghent |
| `NAP` | Naples–Pompeii–Amalfi | Pompeii or Sorrento |
