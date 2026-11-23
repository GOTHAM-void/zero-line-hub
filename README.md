# PlusFlow Clinic Hub

Single-file clinical operating system + backend starter kit implementing the full **8-step Clinic Management Workflow**:
1. **Registration** (Unique Cloud ID `CLD-XXXX`)
2. **Appointment Scheduler** (Slot booking, conflict checks, 1-click Check-In → Token)
3. **Check-in & Live Queue** (QR Walk-in Standee, priority queue, zero-PII `?track=` portal)
4. **Consultation** (Doctor EHR, Allergy Guard, Smart Templates, Voice Rx)
5. **Lab Tests (EHR ↔ Labs)** (Ordered → Sample Collected → Result Ready auto-synced to EHR)
6. **Prescription (EHR → Pharmacy)** (Atomic Firestore stock deduction, Paid-Only Exit Gate)
7. **Billing & Payment** (Front Desk counter, GST CSV, HMAC-verified Razorpay webhooks)
8. **Follow-up & Notifications** (WhatsApp Cloud API / Twilio / SendGrid worker)

## Repository Layout
- `index.html` — Production-hardened single-file frontend (Warm Cream + Botanical Olive/Oat/Terracotta button palette & Matte Black toggle; zero hardcoded API keys).
- `firestore.rules` & `firestore.indexes.json` — Fail-closed RBAC rules and composite indexes for `tokens`, `appointments`, `lab_orders`, `prescriptions`, `medicines`, `payments`, `audit_logs`, and `consent_records`.
- `firebase.json` — Firebase CLI config (`firebase deploy --only firestore`).
- `backend/` — Express + TypeScript starter kit (`server.ts`, `firebaseAuth.ts`, `razorpayWebhook.ts`, `notificationsWorker.ts`).
- `.gitignore`, `.env.example`, `config.example.js` — Strict API-key hygiene templates.

## Deploy Frontend (GitHub Pages)
1. Unzip and push all files to your GitHub repository root.
2. Open **Settings → Pages → Deploy from a branch** (`main`, `/ (root)`).

## Deploy Backend & Keep API Keys Hidden
1. Copy `.env.example` to `.env` locally (never commit `.env` or service account JSONs — both are blocked by `.gitignore`).
2. Deploy Firestore rules/indexes: `firebase deploy --only firestore`
3. Run backend: `cd backend && npm install && npm run build && npm start`
