# Arthanesia

Arthanesia is being rebuilt as a native Android financial planner for Indonesian micro and small businesses.

## Android app

The native Android project is in `android/` and uses Kotlin + Jetpack Compose.

### Build a debug APK

Requirements: JDK 17, Android SDK Platform 37, Android Build Tools 36.0.0, and Gradle 9.3.1.

From the repository root:

```bash
gradle --no-daemon -p android :app:assembleDebug
```

Output:

`android/app/build/outputs/apk/debug/app-debug.apk`

GitHub Actions automatically builds this APK when Android project files are pushed to `main`. The resulting `arthanesia-debug-apk` is uploaded as a workflow artifact.

## Current native prototype scope

- Native Jetpack Compose screens and navigation
- Wallet-purple Arthanesia identity
- Demo entry screen
- Financial overview and ArthaScore placeholder
- Local transaction entry, filtering, and deletion
- Basic expense analysis
- Business savings goals
- Zakat calculator with selectable 250g / 85g nisab and manual gold-price input
- Local rule-based Artha Assistant
- Android speech-recognition launch for VoiceCash
- Currency preference and light/dark theme

Live gold pricing, live FX conversion, Gemini API proxy, Supabase authentication and sync, durable secure multi-user storage, and CSV/PDF export are not connected yet. The zakat calculator deliberately does not display a fabricated live gold quote.
