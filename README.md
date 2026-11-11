# Cyber-Deck-Builds

Cyber deck builds and portfolio.

## Layout

```
sbc/          Every single-board computer I own, by family (see sbc/README.md)
  catalog.csv   Source of truth for boards
  INDEX.md      Generated summary
  <family>/     One folder per SBC family
decks/        One folder per cyber deck build (see decks/README.md)
  _template/    Copy this to start a new build
tools/        Helper scripts
  build_sbc_index.py   Validates the catalog and regenerates sbc/INDEX.md
```

## Quick start

```bash
# After editing sbc/catalog.csv
python3 tools/build_sbc_index.py

# Start a new deck build
cp -r decks/_template decks/<build-name>
```
