# Fin-CM-Blmbrg

Blmbrg - member of the [Fin-CM](https://github.com/diegonmarcos/Fin-CM) hub. No content yet: this repo is a README plus the deployer wiring skeleton (ticket #1224).

Content: `src/fin-terminal`, `src/market_watch`, `src/news`, moved with history from Projects-labtools `b-Nxs_Blmmbrg` (#1257).

## Wiring

- `build.json` (empty build list), `build.sh` and `ship.yml` are symlinks/files that resolve through `1_cicd` and `.github` into the `0_deployer` submodule (diegonmarcos.github.io, shallow, `ignore = all`), as in every front repo (#1192/#1196).
- The deployer clones this repo and overlays it at `a_Companies/blmbrg`; the project is skipped until `dist/` exists. Its published URL will be `https://diegonmarcos.github.io/blmbrg/`.
