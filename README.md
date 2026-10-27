# Fin-CM-Blmbrg

Blmbrg - member of the [Fin-CM](https://github.com/diegonmarcos/Fin-CM) hub. No content yet: this repo is a README plus the deployer wiring skeleton (ticket #1224).

Candidates for the pending front-labtools split (#1218), NOT moved now: front-labtools b-Nxs_Blmmbrg/fin-terminal (fin-term, URL /fin-terminal/), b-Nxs_Blmmbrg/market_watch (market watch, /market_watch/), b-Nxs_Blmmbrg/news (/news/).

## Wiring

- `build.json` (empty build list), `build.sh` and `ship.yml` are symlinks/files that resolve through `1_cicd` and `.github` into the `0_deployer` submodule (diegonmarcos.github.io, shallow, `ignore = all`), as in every front repo (#1192/#1196).
- The deployer clones this repo and overlays it at `a_Companies/blmbrg`; the project is skipped until `dist/` exists. Its published URL will be `https://diegonmarcos.github.io/blmbrg/`.
