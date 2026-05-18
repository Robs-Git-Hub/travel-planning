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

## `croatia_travel_friction.csv`

This dataset is a country-level enrichment file for Croatian destination airports. It adds access/friction, budget-airline, wow-factor, and experience-scoring fields.

| Field | Meaning | Notes |
|---|---|---|
| `airport_iata` | Three-letter IATA code for the destination airport. | Stable airport identifier. |
| `airport_name` | Human-readable airport name. | Matches the airport name used in the master destination ecosystem file where possible. |
| `country` | Country where the airport is located. | For this file, all rows are `Croatia`. |
| `destination_ecosystem` | The wider long-weekend visitor area associated with the airport. | Examples: `Dubrovnik–Cavtat`, `Istria: Pula–Rovinj–Poreč`. |
| `anchor_place` | The specific main place used for measuring airport access and travel friction. | Usually the place a visitor would stay in or travel to first. It may differ from the airport city. |
| `transfer_time_min` | Estimated travel time from the airport to the anchor place, in minutes. | Approximate working estimate for scoring, not a guaranteed journey time. |
| `transfer_mode` | Main transfer mode or modes from airport to anchor place. | Examples: `taxi`, `airport bus or taxi`, `taxi or local bus`. |
| `transfer_complexity` | Qualitative friction of the transfer. | Suggested values: `simple`, `moderate`, `difficult`. |
| `distance_score` | Score for airport-to-anchor convenience. | 1–10 score. Short, simple transfers score highest; destinations above 45 minutes should score lower. |
| `budget_airlines` | Budget or leisure airlines identified as serving the airport from London/UK-oriented sources. | Working draft; airline schedules are seasonal and change frequently. |
| `best_wow_factor` | The strongest standout appeal of the destination ecosystem. | Short descriptive phrase, e.g. dramatic scenery, old town, coastline, architecture, heritage. |
| `wow_score` | Strength of the destination's immediate visual/emotional appeal. | 1–10 subjective score. |
| `walkability_score` | How easy the anchor place is to enjoy without a car. | 1–10 subjective score. |
| `scenic_culture_score` | Combined strength of scenery, architecture, history, culture, or heritage. | 1–10 subjective score. |
| `calmness_score` | How calm, relaxed, and psychologically low-stress the destination feels. | 1–10 subjective score. |
| `tourism_balance_score` | Fit with “tourist-friendly but not overly touristy.” | 1–10 subjective score; lower scores indicate overtourism or weak visitor setup. |
| `overall_match_score` | Composite fit for the long-weekend destination model. | 1–10 working score based on access, wow factor, walkability, calmness, tourism balance, and overall experience fit. |
| `notes` | Free-text explanation or caveat. | Used for context, alternatives, and uncertainty. |

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

### Wow factor

The strongest immediate reason a destination might feel special or memorable. This can come from scenery, architecture, historic atmosphere, dramatic setting, waterfront character, food/café culture, or a distinctive local identity.

### Budget airlines

For this project, `budget_airlines` is a practical travel-planning field rather than a strict aviation-industry classification. It includes low-cost and leisure carriers relevant to affordable London/UK-origin travel, such as easyJet, Ryanair, Wizz Air, Jet2.com, and TUI Airways where applicable.

## Planned future fields

These fields may be added later as the project expands beyond Croatia.

| Field | Meaning | Notes |
|---|---|---|
| `weather_best_months` | Months when the destination best matches the preferred weather band. | Especially spring and early autumn. |
| `typical_shoulder_temp_c` | Approximate shoulder-season daytime temperature. | Useful for warm-but-not-too-hot filtering. |
| `flight_time_min` | Approximate London-to-airport flight time. | Useful for long-weekend practicality. |
| `route_seasonality` | Whether routes are year-round or seasonal. | Important for avoiding false positives. |
| `source_notes` | Notes on data sources used for route, transfer, or scoring claims. | Helpful because routes and schedules change frequently. |
