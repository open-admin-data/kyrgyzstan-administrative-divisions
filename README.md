# Kyrgyzstan Administrative Divisions / Кыргыз Республикасы

Open dataset of Kyrgyzstan's administrative hierarchy — 9 regions, 53 districts, and 460 settlements. This repository provides structured, bilingual (Kyrgyz/Cyrillic + English) reference data with geographic coordinates and postal codes at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| Region | 9 |
| District | 53 |
| Settlement | 460 |
| Coordinates | ✅ Included (all levels) |
| Postal Codes | ✅ Included (settlement level) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-05-27 |
| Website | [openadmindata.org/kg](https://openadmindata.org/kg/) |
| API | [openadmindata.org/api/kg](https://openadmindata.org/api/kg/) |

## Browse by Region

| # | Region | Districts | Settlements | Link |
|---|----|----|----|------|
| 1 | Баткен (Batken) | 6 | 34 | [Browse](divisions/batken-kg05/) |
| 2 | Бишкек ш. (Bishkek (city)) | 0 | 0 | [Browse](divisions/bishkek-city-kg11/) |
| 3 | Чүй (Chui) | 9 | 113 | [Browse](divisions/chui-kg08/) |
| 4 | Ысык-Көл (Issyk-Kul) | 7 | 63 | [Browse](divisions/issyk-kul-kg02/) |
| 5 | Жалалабат (Jalal-Abad) | 13 | 75 | [Browse](divisions/jalal-abad-kg03/) |
| 6 | Нарын (Naryn) | 6 | 60 | [Browse](divisions/naryn-kg04/) |
| 7 | Ош (Osh) | 7 | 79 | [Browse](divisions/osh-kg06/) |
| 8 | Ош ш. (Osh (city)) | 0 | 0 | [Browse](divisions/osh-city-kg21/) |
| 9 | Талас (Talas) | 5 | 36 | [Browse](divisions/talas-kg07/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-region.json](data/all-region.json) | JSON | All 9 region records |
| [all-district.json](data/all-district.json) | JSON | All 53 district records |
| [all-settlement.json](data/all-settlement.json) | JSON | All 460 settlement records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-2 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-region.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-region.json", "utf-8"));
console.log(`Total: ${data.length} regions`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=region, 2=district, 3=settlement |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{region-slug}/
divisions/{region-slug}/{district-slug}/
```

Settlements are listed inline in each district's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-region links
- [Per-region data](docs/llms-full/) — Full data by region

## Citation

```
Kyrgyzstan Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/kyrgyzstan-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
