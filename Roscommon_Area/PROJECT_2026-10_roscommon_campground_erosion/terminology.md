# Terminology

Approved and discouraged terms for this project. Applies to `project.md` (my working plan) and `jason_proposal.md` (the in-field proposal for Jason and his crew). `dnr_letter.txt` and `images/descriptions.md` were already sent, so they are left as written.

## Canonical Location

Use these exact values everywhere. Coordinates come from the photo GPS data sent to Jason.

- Coordinates: 44.4283167, -84.6535861
- Plus Code, full: 86PQC8HW+8H (works pasted alone into Google Maps search)
- Plus Code, short: C8HW+8H Roscommon, MI (the town is required)
- Map by coordinates: <https://www.google.com/maps?q=44.4283167,-84.6535861>
- Map by Plus Code: <https://www.google.com/maps?q=86PQC8HW%2B8H>
- Sanity check: the pin should sit on The Cut, south of Roscommon, at the south end of Everett Road. If a typed code lands elsewhere, use the links instead.

Rules:

- Decimal `lat, lon`, negative longitude for West. Google Maps requires latitude first in `q=`, so `q={lat},{lon}`.
- In a URL, encode the `+` in a Plus Code as `%2B`.
- Never give a bare short code (`C8HW+8H`). Google Maps cannot resolve it without a nearby town. Give the full code, or the short code plus "Roscommon, MI".
- Verified with the reference Open Location Code library: `86PQC8HW+8H` decodes to 44.42831, -84.65356, within about 1 m of the photo GPS point.
- Typo tolerance: Plus Codes have no checksum. A typo in the last two characters (after the `+`) moves the pin a few meters. A typo in the first eight moves it kilometers. Case and spaces do not matter.
- Most forgiving to type: the short code plus the town, because the town search tolerates misspelling and the town supplies the leading digits.
- Always give the links and the sanity-check line, so a mistyped code is noticed and fixed.
- Superseded: the earlier note "44.4281, -84.6536 (C8HW+6HW)" is about 25 m from the photo GPS point.

## Places and Features

| Concept               | Use                              | Avoid                                       |
|-----------------------|----------------------------------|---------------------------------------------|
| The way vehicles use  | two-track                        | road, trail, path, driveway, access road    |
| Its travel surface    | tread                            | road surface, roadbed, road bed, pavement   |
| Its sides             | two-track edge, shoulder         | road edge, roadside                         |
| Uphill, downhill      | uphill edge, downhill edge       | up-road, down-road, road side               |
| Proper name           | Everett Road (name only)         | "the road" for the two-track                |
| The stream            | The Cut                          | the creek, the river (Cut River: maps only) |
| The erosion channel   | gully                            | ditch, ravine, wash                         |
| Advancing erosion     | headcut                          | waterfall, head procession                  |
| Water's route         | flow path                        | drainage (ambiguous), runoff path           |
| Water arriving evenly | sheet flow, "arrives as a sheet" | spreading, dispersing                       |
| Soil                  | clean sand                       | dirt, mud, silk (dictation for silt)        |

## Framing

Jason's work is improvement and maintenance, not answering complaints. Frame the site as a work item.

- Use: erosion site, work site, work item, location, opportunity to fix early.
- Avoid: problem, complaint, issue, disaster, failure (except "failure modes" as a design term).

## Structures

| Concept                 | Use                                 | Avoid                                      |
|-------------------------|-------------------------------------|--------------------------------------------|
| Crossing at the gully   | hardened dip, broad dip             | water bar, lead-out, turnout (they divert) |
| Brush dam               | brush check dam                     | damn, "dam" alone, beaver dam              |
| Board steps             | board weir                          | wier, fish ladder, waterfall               |
| Low point in a dam      | center notch                        | spillway, flaking                          |
| Pin at headcut lip      | hard sill (log or stone)            | plug, wall                                 |
| Rock or brush below dam | armored landing                     | apron, splash pad                          |
| Sand leak barrier       | filter layer (coir, burlap, fabric) | liner, seal, "silt will seal it"           |
| Temporary bags          | sandbags, temporary only            | sandbag dam, sandbag bridge                |

## Failure Modes

Use these names. They are hazards, not features.

- flanking (not "flaking")
- undercutting and piping
- plunge-pool scour (the hazard; design so none forms)
- surge overtopping
- sediment fill

## People and Process

| Concept           | Use                                             | Avoid                                |
|-------------------|-------------------------------------------------|--------------------------------------|
| Jason's title     | Forest Manager                                  | Unit Manager, the boss               |
| Jason's team      | Jason, your crew                                | the guys, staff (in proposal)        |
| Me                | volunteer, co-author                            | expert; "amateur" only once, lightly |
| The AI            | Claude (an AI assistant), co-author             | the bot, the AI (unqualified)        |
| Land ownership    | "coordinate with the appropriate organizations" | asking Jason who owns it             |
| My working plan   | project plan (`project.md`)                     | "the proposal"                       |
| What Jason gets   | in-field proposal                               | "the letter" (`dnr_letter.txt`)      |
| Unverified claims | "a guess for your crew to confirm"              | stating them as fact                 |

## Photos

Orientation comes from pixel dimensions (wider than tall is landscape), never from memory. `make info` prints this table from the files. `images/descriptions.md` was already sent and calls IMG_7478 "portrait"; it is landscape.

| File              | Pixels (web quality) | Orientation |
|-------------------|----------------------|-------------|
| IMG_7473.jpeg     | 1200 x 900           | landscape   |
| IMG_7474.jpeg     | 900 x 1200           | portrait    |
| IMG_7475.jpeg     | 900 x 1200           | portrait    |
| IMG_7476.jpeg     | 1200 x 900           | landscape   |
| IMG_7478.jpeg     | 1200 x 900           | landscape   |
| location_map.jpeg | 996 x 938            | landscape   |

Folders: `images/` holds originals, `images/web_quality/` holds the 1200 px, JPEG 70 copies made by `make images`.

## Signs

Avoid "sign" and "signage" as a fix. A sign is a crutch for a design that does not already tell people how to use it. The two-track should make the right use the easy use.

- Discouraged: sign, signage, "Slow" placard, notice board.
- Approved: design cue, physical constraint, obvious route, desire line, "make the right route the easy one."
- Method: place logs or boulders so the hardened dip is the only comfortable path. Harden the surface drivers should use. Do not rely on words.
- Sources: Steve Krug, *Don't Make Me Think*. Don Norman, *The Design of Everyday Things* (originally *The Psychology of Everyday Things*): affordances, constraints, forcing functions.

## Units and Style

- Measurements: `6-12 in`, `2:1`, `30 ft`, `25 m` with a plain number, no `~`.
- Prose paragraphs on one long line. Tables stay within 120 columns.
- Cross-reference by filename in backticks.
