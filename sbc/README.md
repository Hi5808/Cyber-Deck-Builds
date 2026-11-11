# SBC Collection

Every single-board computer (SBC) I own or have won, sorted by family.

## Where things live

| Path | Purpose |
|------|---------|
| `catalog.csv` | **Source of truth.** One row per board. Edit this file. |
| `INDEX.md` | Generated summary (counts per family, full table). Do not edit by hand. |
| `<family>/` | Notes, datasheets, photos, and specs for boards in that family. |

Regenerate the index after editing the catalog:

```bash
python3 tools/build_sbc_index.py
```

The script also validates the catalog. It fails if a row uses an unknown family, tier, or status, or if an `id` is duplicated.

## Families (categories)

Each folder under `sbc/` is one family. The `family` column in `catalog.csv` must match a folder name exactly.

| Folder | What belongs here |
|--------|-------------------|
| `raspberry-pi` | Raspberry Pi boards (Zero, 3, 4, 5, Pico-class if Linux-capable, etc.) |
| `orange-pi` | Orange Pi boards |
| `banana-pi` | Banana Pi / BPI boards |
| `rockchip` | Rockchip-based boards from any vendor (RK3566, RK3588, etc.) |
| `allwinner` | Allwinner-based boards (H3, H5, H616, etc.) |
| `amlogic` | Amlogic-based boards (S905, S922, etc.) |
| `nvidia-jetson` | Jetson Nano, Orin, Xavier, and other Jetson modules/dev kits |
| `x86` | x86/amd64 mini boards and SBC-style PCs (e.g., Intel/AMD small boards) |
| `microcontroller` | MCU boards with no full Linux (ESP32, RP2040, STM32, etc.) |
| `other` | Anything that does not fit above. Move it when a new family gets 3+ boards. |

## Tiers

The `tier` column rates what a board is good for in a deck build.

| Tier | Meaning | Examples |
|------|---------|----------|
| `mcu` | Microcontroller, no full OS | ESP32, RP2040 |
| `entry` | Low power, 512 MB to 2 GB RAM, light tasks | Pi Zero 2 W, Orange Pi Zero |
| `mid` | 2 to 8 GB RAM, general Linux, most deck builds | Pi 4, Pi 5 (4 GB), Orange Pi 5 |
| `high` | 8 GB+ RAM, GPU/NPU, heavy workloads | Jetson Orin, Pi 5 (8 GB+), RK3588 boards |

## Status values

| Status | Meaning |
|--------|---------|
| `owned` | In my possession, not assigned to a build |
| `in-deck` | Installed in a build (set `deck` to the build's folder name) |
| `spare` | Kept as a backup or for testing |
| `for-sale` | Listed for sale or trade |
| `gone` | Sold, traded, or given away (keep the row for history) |

## Adding a board

1. Add a row to `catalog.csv`. Use a unique `id` such as `RPI-4B-02` or `OPI-5-01`.
2. Put any datasheets or photos in the matching family folder.
3. Run `python3 tools/build_sbc_index.py`.
4. Commit `catalog.csv`, `INDEX.md`, and the new files.

## Catalog columns

| Column | Description |
|--------|-------------|
| `id` | Unique ID for this physical board |
| `family` | Folder name under `sbc/` |
| `model` | Board name, e.g., `Raspberry Pi 4 Model B` |
| `soc` | System-on-chip, e.g., `BCM2711` |
| `ram_gb` | RAM in GB |
| `storage` | Built-in storage, e.g., `eMMC 32GB` or `none` |
| `tier` | `mcu`, `entry`, `mid`, or `high` |
| `status` | See status values above |
| `acquired_from` | Where it came from, e.g., giveaway name or store |
| `acquired_date` | `YYYY-MM-DD` |
| `deck` | Build folder under `decks/` if `status` is `in-deck`, else blank |
| `notes` | Free text |
