---
name: korean-real-estate
description: >-
  Answer Korean real-estate and building questions via Agent Store — building
  registry & permits, assessed price history, apartment transactions, and new-home
  subscriptions — starting from an address. Use for property research, building
  history, apartment prices, or subscription schedules in Korea.
  Connect: https://agent.store/mcp
---

# Korean real estate & buildings

Most flows start from an address; normalize it first.

## Flow
1. **Resolve the address** — `geocoder__geo_address_to_coord` (or
   `address_search__juso_search_address`) → coordinates; `archhub__find_region` →
   legal-dong region code (needed by many tools).
2. **Building facts** — `archhub__building_profile` (the integrated card), then as needed
   `archhub__building_floors`, `archhub__parcel_history` (timeline), `archhub__price_history`
   (assessed price), `archhub__seismic_check`, `archhub__permits_pipeline`, `archhub__old_buildings`.
3. **Apartment market** — `apartment__apt_sale_transactions` for actual sale prices;
   `apartment__apt_basic_info` / `…_detail_info` and the `apt_list_by_*` finders for a complex.
4. **New-home subscriptions** — `apply_home__applyhome_apt` (+ `…_apt_unit_types`),
   `applyhome_officetel`, `applyhome_public_private_rent`, `applyhome_remnant` for schedules/types.

## Tips
- Always geocode/region-resolve before tools that need a region or PNU code.
- For "is this building old / seismic-safe?" use the dedicated archhub tools, don't infer.
- Cite the source (MOLIT ArchHUB / actual-transaction price / REB Cheongyak Home).
