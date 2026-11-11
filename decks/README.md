# Deck Builds

One folder per cyber deck build. Start new builds by copying `_template/`.

```bash
cp -r decks/_template decks/<build-name>
```

Use a short, lowercase, hyphenated name, e.g., `pi5-portable-deck`.

## Build folder layout

| File / folder | Contents |
|---------------|----------|
| `README.md` | Build write-up: goal, boards used, status, and lessons learned |
| `bill-of-materials.csv` | Every part in the build, with cost and source |
| `photos/` | Build photos and final shots |

## Linking boards to builds

A board's `sbc/catalog.csv` row should show:

- `status` = `in-deck`
- `deck` = the build folder name, e.g., `pi5-portable-deck`

Run `python3 tools/build_sbc_index.py` after changing the catalog.

## Builds

| Build | Status | Main SBC | Notes |
|-------|--------|----------|-------|
| _(none yet)_ | | | |
