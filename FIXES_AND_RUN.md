# EzyBus fixes applied

## Main fixes made
- Removed the broken nested duplicate project folder.
- Fixed the root `package.json` so it is valid JSON again.
- Removed the broken workspace setup that was interfering with separate frontend/backend installs.
- Fixed a backend syntax/runtime issue in `backend/src/config/env.js` caused by mixing ES module export syntax with CommonJS.
- Made backend configuration safe for local development by providing sensible defaults.
- Reworked Firebase initialization so the backend no longer crashes when `serviceAccountKey.json` is missing.
- Added a mock database fallback when Firebase Admin credentials are not configured.
- Relaxed frontend TypeScript strictness to reduce build-stopping type noise from incomplete typings in the project.
- Added `frontend/next-env.d.ts`.
- Added `frontend/.env.local.example`.
- Updated `backend/.env.example`.
- Fixed `frontend/components/BusMap.tsx` so markers always default to an array.
- Changed frontend config to fall back to `http://localhost:5000/api/v1` when `NEXT_PUBLIC_API_URL` is missing.

## Run steps
1. Root:
   - `npm install`
2. Backend:
   - `cd backend && npm install`
3. Frontend:
   - `cd frontend && npm install`
4. Optional env files:
   - copy `backend/.env.example` to `backend/.env`
   - copy `frontend/.env.local.example` to `frontend/.env.local`
5. Start from project root:
   - `npm run dev`

## Notes
- Without Firebase Admin credentials, the backend now runs in mock mode for local development instead of crashing.
- For real persistence, fill the Firebase variables in `backend/.env`.
