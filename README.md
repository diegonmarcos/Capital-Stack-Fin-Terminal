# Fin-CM-Blmbrg

Blmbrg - member of the [Fin-CM](https://github.com/diegonmarcos/Fin-CM) hub. No content yet: this repo is a README plus the deployer wiring skeleton (ticket #1224).

Content moved with history from Projects-labtools `b-Nxs_Blmmbrg` (#1257), laid out as FIN TERMINAL (#1279).

## FIN TERMINAL

| Display name | Folder | Notes |
|---|---|---|
| CentralBank | `src/CentralBank` | pointer only; code lives in Fin-CM-mqpm `src/central_bank` |
| Fin Terminal | `src/Fin-Terminal` | formerly `src/fin-terminal` |
| GDELT News | `src/GDELT-News` | GDELT feed dashboard, formerly `src/news` |
| MarketWatch | `src/MarketWatch` | formerly `src/market_watch` |
| Data Science & ML Terminal | `src/DataScience-ML-Terminal` | new, purpose placeholder |

## Wiring

- `build.json` (empty build list), `build.sh` and `ship.yml` are symlinks/files that resolve through `1_cicd` and `.github` into the `0_deployer` submodule (diegonmarcos.github.io, shallow, `ignore = all`), as in every front repo (#1192/#1196).
- The deployer clones this repo and overlays it at `a_Companies/blmbrg`; the project is skipped until `dist/` exists. Its published URL will be `https://diegonmarcos.github.io/blmbrg/`.
