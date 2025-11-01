<!-- Short, actionable instructions for AI coding agents working on this repository -->
# Copilot instructions — contactbook-backend

This repo is a small Node.js/Express backend. Below are the facts and focused instructions an AI coding agent should use to make productive, low-risk changes.

Key facts (from package.json)
- Project name: `contactbook-backend`
- Entry / runtime: `npm start` runs `nodemon serve.js` (note: package.json `main` points to `index.js` but the start script uses `serve.js`). Check which of those files exist before editing.
- Module type: `commonjs` — use `require()` / `module.exports`, not ES modules.
- Framework: `express` (dependency present)
- Dev tooling: `eslint` and `prettier` are included as devDependencies.
- Tests: `test` script is a placeholder (no tests configured).

Primary goals for edits
- Keep CommonJS style and the existing startup script intact. If you add a new server entry or change start behavior, update `package.json` scripts accordingly.
- Avoid introducing ES module syntax (import/export) unless you also update `type` in `package.json` and adapt the rest of the codebase.

Where to look first
- Root: check for `serve.js` and `index.js` (startup files referenced by `scripts`/`main`).
- If present, inspect any `routes/`, `controllers/`, `models/`, or `middleware/` folders for request handling patterns.

Developer workflows (what to run locally)
- Install dependencies:
```powershell
npm install
```
- Start in dev mode (uses nodemon per package.json):
```powershell
npm start
```
- Lint and format checks (use these before pushing):
```powershell
npx eslint .
npx prettier --check .
```

Conventions and constraints
- Use CommonJS `require()` and `module.exports` throughout.
- Follow existing code formatting enforced by `prettier` and `eslint` (autofix where safe).
- Tests are not present—don't add large test scaffolding without confirming with maintainers.

Integration points and external dependencies
- Express-based HTTP handlers (see `express` in dependencies).
- Common middleware likely used: `body-parser`, `cors` (both are dependencies) — expect JSON request bodies and CORS handling.

Examples of safe edits (concrete)
- Add a new route: require Express, attach to the app in the existing `serve.js` or `index.js`, and export router via `module.exports = router` if creating a new module file.
- Add ESLint or Prettier fixes: run `npx eslint --fix` and `npx prettier --write` and commit only formatting/lint fixes in separate PR.

What to avoid
- Do not switch the repo to ES modules or change `type` without updating all imports/exports and verifying runtime start script.
- Don’t assume test frameworks or CI are configured; mention if you add tests and update `package.json` scripts.

If you need clarification
- Ask where `serve.js` vs `index.js` should be authoritative for startup. The `start` script currently uses `serve.js`.

Files referenced
- `package.json` — scripts, deps, module type
- `serve.js` or `index.js` — startup
- Any `routes/`, `controllers/`, `middleware/` folders if present

If anything here looks wrong or there are missing files (for example `serve.js` is not present), tell me and I'll update these instructions to match the real file layout.

— End of instructions
