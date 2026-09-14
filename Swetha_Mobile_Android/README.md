# Swetha mobile app

A private Android companion for voluntary feminine self-expression, confidence,
journaling, tasks, check-ins and feminist learning. App records stay on the phone.
AI chat requires internet and a Gemini API key; messages sent for replies are
processed by Google.

## Get an APK using GitHub

1. Upload the **contents of this folder** to a new private GitHub repository.
2. Open **Actions → Build Android APK → Run workflow**.
3. After the green check, open the workflow run and download
   **Swetha-Android-APK** from Artifacts. Extract it to get `app-debug.apk`.
4. Move the APK to your Android phone, open it, and allow installation from that
   source when Android asks. This is a debug build for personal testing.
5. Open Swetha → Settings, enter the Gemini API key and save it. Set a 4–8 digit PIN.

The workflow contains no keys. Never upload `.env`, API keys, or exported app data.
For wider distribution, create a release signing key and use Android Studio's
**Generate Signed Bundle / APK** flow.

## Run as a web app

The `www` folder is a PWA. Serve it over HTTPS and use Chrome's **Add to Home
screen**. Opening `index.html` directly supports most features, but browser rules
may restrict service workers or API access.

## Data and limitations

- Check-ins, journals, tasks, chat history, settings and API key use WebView local
  storage. They do not sync across phones.
- The PIN is a convenience lock. Android device encryption and a screen lock remain
  necessary; a person with advanced device access may recover local data or the key.
- Export deliberately excludes the API key and PIN. Delete All clears this app's
  local records, not Telegram or Google provider records.
- Uninstalling or clearing app storage deletes local records.
- AI replies can be wrong. Medical transition decisions belong with a qualified,
  gender-affirming clinician. This app does not prescribe treatment.
- Photo generation is not included in this first mobile build because embedding a
  reusable Gemini key in a client-side image workflow needs additional account and
  model testing. The local journal, tasks and check-ins work offline; AI chat does not.

## Local Android build

Install Android Studio / SDK 35 and Gradle 8.11.1, then run from `android`:

```bash
gradle assembleDebug
```

The APK will be at `android/app/build/outputs/apk/debug/app-debug.apk`.
