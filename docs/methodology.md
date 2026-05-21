# Methodology

## Data Sources

- **OCHA COD-AB Kyrgyzstan** (CC BY-IGO) — 9 regions, 53 districts, 460 settlements with P-codes, centroid coordinates, and trilingual names (English + Russian + Kyrgyz)
- **Kyrgyz Post** (post.kg) — Postal codes matched by village name and district center codes

## Processing

1. Administrative records from OCHA COD-AB XLSX gazetteer with Kyrgyz names from `name2` column
2. Removed 277 settlement entries with no names (empty rows in source data)
3. Postal codes matched from post.kg: village-specific where name matches, district center (XX00) as fallback
4. Multi-format export: JSON, NDJSON, CSV

## Accuracy

- Coordinates: 100% at all levels (from OCHA COD-AB centroids)
- Kyrgyz (Cyrillic) names: 100% at all levels
- Postal codes: 100% (160 village-specific + 300 district-center fallback)
- Build script is idempotent: same input always produces same output