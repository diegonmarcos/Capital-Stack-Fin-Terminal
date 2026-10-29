# Fin Terminal

Display name: **Fin Terminal**, part of FIN TERMINAL.

## Brief

Bloomberg-terminal-style web frontend for fin-api (formerly `fincept-server`): REST and WebSocket panels, built with the repo `build.json`/`ship.yml` conventions. Formerly `src/fin-terminal`. The original project notes follow below.

## FOSS references

Existence of each repository checked with `git ls-remote` on 2026-10-29. Licences as published upstream; re-check before reuse.

- [OpenBB-finance/OpenBB](https://github.com/OpenBB-finance/OpenBB): Open-source investment research platform and terminal (AGPL-3.0)
- [ghostfolio/ghostfolio](https://github.com/ghostfolio/ghostfolio): Open-source wealth management software (AGPL-3.0)
- [ranaroussi/yfinance](https://github.com/ranaroussi/yfinance): Yahoo Finance market data downloader (Apache-2.0)
- [ccxt/ccxt](https://github.com/ccxt/ccxt): Unified crypto exchange trading and data API (MIT)
- [mrjbq7/ta-lib](https://github.com/mrjbq7/ta-lib): Python wrapper for the TA-Lib technical analysis library (BSD-2-Clause)
- [bukosabino/ta](https://github.com/bukosabino/ta): Technical analysis indicators for pandas (MIT)
- [AI4Finance-Foundation/FinGPT](https://github.com/AI4Finance-Foundation/FinGPT): Open-source financial large language models (MIT)

## Original project notes


Bloomberg-terminal-style web frontend for **fin-api** (formerly `fincept-server`).

- **API**: `https://api.diegonmarcos.com/fin-api/*` — REST + WebSocket
- **Port (dev)**: 8024
- **Stack**: Vanilla TypeScript + SCSS, declarative `build.json` (sass + esbuild + copy + symlink)

### Design

Authentic Bloomberg aesthetic — **amber on true black**, hard rectangles, monospace everywhere, dense layout, function-key bar, command bar, status bar.

Two themes (runtime-switchable, `Ctrl+T`):
1. `bloomberg-dark` (default) — `#000000` background, `#FFA028` Sunshade amber
2. `egui-dark` — GitHub-dark palette, copied verbatim from the egui desktop's `assets/themes/dark.json`

### Source of truth

These three JSON files are **copies** of the fin-api source-of-truth, guarded by a CI diff test:

- `src/typescript/data/screen-specs.json` ← `fin-api/src/code/screen-specs.json`
- `src/typescript/data/palette-egui-dark.json` ← `fin-api/src/code/assets/themes/dark.json`

If the fin-api source changes, the diff test fails and we must update the copies.

### Build

```bash
./build.sh build      # production bundle
./build.sh dev        # dev server (auto-rebuild on change)
npm test              # vitest
```

### Layout (mirrors `sailytics/`)

```
src/
├── index.html
├── public/                       # static (served as-is)
├── scss/
│   ├── main.scss
│   ├── abstracts/_*.scss         # vars, mixins
│   ├── base/_*.scss              # reset, typography
│   ├── components/_*.scss        # widgets, charts
│   ├── layout/_*.scss            # shell, panel, command-bar, function-bar, status-bar
│   └── utilities/_*.scss
└── typescript/
    ├── main.ts
    ├── data/                     # JSON sources (palettes, specs, registry, F-keys)
    ├── api/                      # REST + WS client + types
    ├── shell/                    # theme, command-bar, panel, function-bar, status-bar
    ├── widgets/                  # ticker, data-table, loading-overlay
    ├── charts/                   # candlestick (lightweight-charts), line (canvas)
    └── screens/                  # 41 spec + 10 custom + registry
```
