# CB8 Radiator Design

Parameterized cooling system model for CU Boulder Racing Team's Formula SAE car, CB8.

## What this does

Models radiator heat rejection as a function of RPM, vehicle speed, and airflow, replacing a legacy steady-state notebook that carried several outdated assumptions:

- Fan-only or fixed-airflow assumptions, replaced with a combined ram-air + fan velocity model (`u_eff = √(u_ram² + u_fan²)`)
- 100% of engine heat routed to coolant, corrected to reflect actual exhaust heat rejection split
- No accounting for the fuel switch from gasoline to E85
- Missing dual-pass radiator configuration (the team has always run dual-pass; the old model only supported single-pass)

## Structure

- **Config** — geometry, temperatures, expected heat load (from Realis), shift points, fan settings. Edit here for a new car/config.
- **Physics & solver** — air/water property correlations, radiator geometry calculations, core heat transfer solver. No edits needed.
- **Comparison & plotting** — expected vs. modeled heat rejection, gear-by-gear FOS maps, shift point evaluation.

## Key outputs

- Radiator heat rejection vs. RPM, benchmarked against Realis expected heat load
- FOS across every gear, at both RPM and equivalent vehicle speed, fan-on vs. fan-off
- Support for single-pass or dual-pass radiator configurations

## Usage

Edit the Config cell (geometry, expected heat dict, shift points), then re-run. No file save needed between edits.

## Context

Built to revalidate CB7's actual cooling margin ahead of CB8's sidepods project — see [portfolio writeup] for the full story.
