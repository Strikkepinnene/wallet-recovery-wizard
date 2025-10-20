# Copilot Instructions for BitGo Wallet Recovery Wizard

## Project Overview
This is an Electron + Vite + React application for recovering coins from BitGo wallets, supporting unsigned sweeps, non-BitGo recoveries, and multiple coin types. The app is cross-platform and designed for end-users to recover funds without BitGo involvement.

## Architecture & Key Patterns
- **Frontend:** React (see `src/`), with components in `src/components/` and containers in `src/containers/`.
- **Electron Main/Preload:** Electron entry points in `electron/main/index.ts` and `electron/preload/index.ts`.
- **Coin Logic:** Coin-specific logic and factories in `electron/coinFactory.ts` and related markdown docs (e.g., `ETHW.md`, `EOS.md`).
- **Styles:** Tailwind CSS, with main styles in `src/assets/styles/index.css` and `src/components/index.css`.
- **Context/State:** React Contexts in `src/contexts/`, reducers in `src/reducers/`, and hooks in `src/hooks/`.
- **Utilities:** Shared helpers in `src/helpers/` and `src/utils/`.

## Developer Workflows
- **Build:** Use Electron Vite React conventions. Main build scripts are in `scripts/` (e.g., `build-icons.js`, `bump-version.ts`).
- **Start (Debug):** Run `node .vscode/.debug.script.mjs` (see VS Code tasks).
- **Test:** E2E tests in `e2e/` (Playwright), unit tests in `src/` (if present). Configs: `playwright.config.ts`, `vitest.config.ts`.
- **Lint/Format:** Uses Prettier and ESLint (see configs in root).

## Conventions & Patterns
- **Coin Onboarding:** Follow `ONBOARD_COIN.md` for adding new coins.
- **Transaction Broadcast:** Each coin has a dedicated markdown doc for broadcast instructions (e.g., `ETHW.md`, `EOS.md`).
- **Recovery Types:** Unsigned sweep, non-BitGo recovery, consolidate recovery—see respective markdown docs for flows.
- **Component Structure:** Prefer colocated styles and stories (see `AlertBanner/AlertBanner.stories.tsx`).
- **Type Safety:** Use TypeScript throughout; shared types in `electron/types.ts` and `src/utils/types.ts`.
- **Context Usage:** Use React Context for global state (see `AlertBannerContext.ts`).

## Integration Points
- **External APIs:** Minimal direct API calls; most logic is local and coin-specific.
- **Markdown Docs:** Key flows and instructions are documented in markdown files in the root directory.
- **Electron IPC:** Communication between renderer and main handled via preload scripts.

## Examples
- To add a new coin, update logic in `electron/coinFactory.ts` and document in a new markdown file.
- For a new recovery flow, create a container in `src/containers/`, add components in `src/components/`, and update context/reducers as needed.

## References
- [ONBOARD_COIN.md](../ONBOARD_COIN.md) — Coin onboarding guide
- [UNSIGNED_SWEEP.md](../UNSIGNED_SWEEP.md) — Unsigned sweep instructions
- [NON_BITGO_RECOVERY.md](../NON_BITGO_RECOVERY.md) — Non-BitGo recovery instructions
- [ETHW.md](../ETHW.md), [EOS.md](../EOS.md), etc. — Coin-specific broadcast instructions

---
_If any section is unclear or missing important project-specific details, please provide feedback to improve these instructions._
