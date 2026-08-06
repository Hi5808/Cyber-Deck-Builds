# CLAUDE.md — Cyber Deck Builds

## What This Repo Is

A personal portfolio and reference archive for custom Cyber Deck builds. Each build documents the hardware components, design decisions, and assembly notes in a consistent, searchable format. The repository is content-driven — no build scripts, no compiled code.

## Intended Workflow

The owner supplies raw component lists or descriptions for each build. Claude's job is to:

1. **Collect** — accept component data in any format the owner provides (prose, bullet lists, part numbers, links, photos descriptions, etc.)
2. **Analyze** — identify component categories, flag gaps or incompatibilities, note power/weight/connectivity implications
3. **Sort & structure** — normalize the data into the standard build format below
4. **Prep** — produce ready-to-commit Markdown files; never require the owner to reformat raw input

Always commit finished build files to the active feature branch and push. Do not wait to be asked.

## Repository Layout (Planned)

```
Cyber-Deck-Builds/
├── CLAUDE.md           # this file
├── README.md           # public-facing intro
├── builds/
│   └── <build-slug>/
│       ├── README.md   # build overview & photos
│       └── components.md  # full component list
└── assets/
    └── <build-slug>/   # images, schematics, etc.
```

Create the `builds/` directory when the first build is added. Use a short kebab-case slug for each build folder (e.g. `rpi5-brutalist-deck`, `v1-clam-shell`).

## Standard Build File Format

### `builds/<slug>/README.md`

```markdown
# <Build Name>

**Status:** Planning | In Progress | Complete
**Form Factor:** <clamshell / monoblock / tablet / open-frame / other>
**Primary Use:** <pentesting / field ops / general computing / display / other>

## Summary
One-paragraph description of the build concept and goals.

## Key Specs
| Property       | Value |
|----------------|-------|
| Compute        |       |
| Display        |       |
| Input          |       |
| Power          |       |
| Connectivity   |       |
| Dimensions     |       |
| Weight         |       |

## Notes
Design decisions, trade-offs, lessons learned.
```

### `builds/<slug>/components.md`

```markdown
# Components — <Build Name>

## Compute
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Display
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Input
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Power
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Connectivity & RF
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Storage
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Enclosure & Hardware
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Cables & Adapters
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Miscellaneous
| Part | Model / SKU | Qty | Source | Notes |
|------|-------------|-----|--------|-------|

## Totals
| Metric | Value |
|--------|-------|
| Estimated Cost | |
| Estimated Weight | |
| Peak Power Draw | |
```

## Component Categorization Rules

When the owner provides a raw parts list, sort each item into the category above using these rules:

- **Compute** — SBCs, MCUs, GPUs, co-processors
- **Display** — screens, touch controllers, display drivers, LCDs/OLEDs
- **Input** — keyboards, trackpads, mice, encoders, buttons
- **Power** — batteries, BMS, chargers, voltage regulators, PoE hats, UPS modules
- **Connectivity & RF** — WiFi/BT adapters, SDR dongles, antennas, Ethernet, USB hubs, cellular modems
- **Storage** — SSDs, SD cards, NVMe drives, USB flash
- **Enclosure & Hardware** — chassis, panels, standoffs, hinges, fasteners, 3D-printed parts
- **Cables & Adapters** — all cables, ribbon connectors, breakout boards that are purely passive
- **Miscellaneous** — fans, thermal pads, LEDs, speakers, anything that doesn't fit above

If a part is ambiguous, place it in the best-fit category and add a note in the Notes column.

## Conventions

- All prices in USD unless noted.
- Use the manufacturer's full model name in the Model/SKU column when known; add part numbers in parentheses if available.
- Source column: retailer name only (e.g. `Amazon`, `Adafruit`, `AliExpress`, `Mouser`), not full URLs.
- Keep Notes concise — one short phrase per cell.
- Build slugs must be lowercase, hyphen-separated, no spaces or special characters.
- Never delete a build folder; set Status to `Abandoned` in its README instead.

## Git Conventions

- Branch naming: `claude/<short-description>` for AI-authored work.
- Commit messages: imperative mood, reference the build slug when applicable.
  - `add rpi5-brutalist-deck component list`
  - `update v1-clam-shell status to complete`
- All AI-authored commits are co-authored with the standard footer.
- Do not force-push `main`.

## AI Assistant Notes

- The owner will provide component data in informal, unstructured form. Normalize it; do not ask for reformatted input.
- When a component is unrecognized, make a best-effort categorization and flag it in Notes as `[verify]`.
- If power budget, weight, or compatibility issues are spotted during analysis, surface them in the build README under Notes — do not silently omit them.
- This repo has no tests, linters, or CI. Skip any checks that would apply to a software project.
- Keep CLAUDE.md up to date as the project evolves — update the layout section when new directories are added.
