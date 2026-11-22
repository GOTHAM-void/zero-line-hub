# PlusFlow Clinic Hub

Single-file clinical operating system uniting Front Desk QR Check-In, Doctor EHR, Paid-Only Pharmacy Dispatch, and real-time Firebase Firestore sync.

## Included Files
- `index.html` — Production-hardened single-file web app (no hardcoded API keys).
- `firestore.rules` — Fail-closed RBAC Firestore security rules with append-only audit & DPDP consent logs.
- `firestore.indexes.json` — Composite Firestore indexes for token queries.
- `firebase.json` — Firebase CLI configuration for deploying rules and indexes.
- `backend/firebaseAuth.ts` — Express RBAC middleware reading credentials from environment variables.
- `.gitignore` — Blocks `.env`, `config.local.js`, service account JSONs, and private keys from being committed.
- `.env.example` & `config.example.js` — Safe placeholder templates for local/server configuration.

## Publish to GitHub Pages
1. Unzip this archive and upload all files to the root of your GitHub repository.
2. In your GitHub repository, open **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**, choose `main` and `/ (root)`, and click **Save**.

## Keep API Keys Hidden
- **Never commit** `.env`, `config.local.js`, or any Firebase Admin `serviceAccountKey.json` file (all are pre-ignored in `.gitignore`).
- Enter your Firebase Web config at runtime inside the app under **Settings & Menu → Admin → Cloud Sync**, or deploy `firestore.rules` and `firestore.indexes.json` with:
  ```bash
  firebase deploy --only firestore
  ```
- Restrict your Firebase Web API key in Google Cloud Console to your GitHub Pages domain (HTTP referrer restriction).
