---
name: commercial-district-analytics
description: >-
  Analyze a Korean commercial district / trade area via Agent Store — count and
  break down stores by industry within a radius, polygon, building, or trade zone,
  starting from an address or coordinates. Use for store density, industry mix, or
  trade-area questions (e.g., "how many cafes within 500m of Gangnam Station").
  Connect: https://agent.store/mcp
---

# Commercial-district & store analytics (sbiz)

The `commercial_district__` family has 20+ spatial tools; pick by the area shape.

## Flow
1. **Resolve the location** — `geocoder__geo_address_to_coord` (address → lat/lng), or use the
   region-code helpers `sbiz_region_sido/sigungu/dong/legaldong`.
2. **Pick the query by area shape:**
   - Around a point/address → `sbiz_store_in_radius` or `sbiz_stores_near_address`
   - Custom area → `sbiz_store_in_polygon` / `sbiz_store_in_rectangle`
   - Administrative area → `sbiz_store_in_admin`
   - A specific building / parcel → `sbiz_store_in_building` / `sbiz_store_in_pnu`
   - A defined trade zone → `sbiz_trade_zone*` then `sbiz_store_in_trade_zone`
3. **Filter by industry** — resolve codes with `sbiz_industry_large/middle/small`, then
   `sbiz_store_by_industry` (e.g., cafés, restaurants).

## Tips
- Geocode first; most spatial tools need coordinates or a region/PNU code.
- For "how many X within Nm", use radius + industry filter; summarize counts, don't dump every row.
- Cite the source (sbiz / Small Enterprise and Market Service).
