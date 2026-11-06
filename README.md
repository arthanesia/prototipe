# Arthanesia

Arthanesia is a financial-management application in development for Indonesian small businesses and UMKM.

## Public product website

- Website: https://arthanesia.github.io/prototipe/
- Admin dashboard concept (synthetic data only): https://arthanesia.github.io/prototipe/admin-preview.html
- Source repository: https://github.com/arthanesia/prototipe

The website is published from `website/` using GitHub Pages.

## Android app

The native Android project is in `android/` and uses Kotlin + Jetpack Compose.

The current debug build is **0.4.0**. It includes:
- Native navigation and financial overview
- Separate manual, voice recognition, and receipt photo/OCR entry methods
- Local transaction filtering and deletion
- A4 bookkeeping report PDF, Android print dialog, and CSV export
- Basic cashflow and category analysis
- Savings goals and zakat/tax estimates
- Local Artha Assistant analysis

The Android project compiles successfully in GitHub Actions. This is still a debug/testing build; it has not been validated on a matrix of physical Android devices.

### Build a debug APK

Requirements: JDK 17, Android SDK Platform 36, Android Build Tools 36.0.0, and Gradle 9.3.1.

From the repository root:

```bash
gradle --no-daemon -p android :app:assembleDebug
```

Output: `android/app/build/outputs/apk/debug/app-debug.apk`

GitHub Actions automatically builds this APK when Android project files are pushed to `main`. The resulting `arthanesia-debug-apk` is uploaded as a workflow artifact.

## Backend and admin status

The connected Supabase account currently has no project available. Therefore, the files in `supabase/` are deployment templates only:
- `schema-blueprint.sql`: user-owned financial records, RLS, limited support access, and audit schema.
- `functions/artha-assistant/`: authenticated Gemini assistant template, with explicit consent and aggregated data only.
- `functions/admin-dashboard/`: admin-only profile directory and aggregate metrics template.
- `admin-preview.html`: visual preview only; it does not access user accounts or production data.

Supabase Auth, database sync, Gemini AI, and a live admin dashboard are **not active** until a project is connected, the schema is deployed and security-tested, and backend secrets are configured.

## Important limitations

- Local records are not yet durably synced across devices or backed by a production cloud database.
- The assistant included in the APK uses local analysis rules; the Gemini function is only a server-side integration template.
- Currency selection is currently a preference, not historical FX conversion.
- PDF/CSV reports use the data currently stored on the device.
- Zakat/tax figures are estimates and should be verified before financial or legal use.

Never put Supabase secret/service-role keys or the Gemini API key in the app, website, or source control.
