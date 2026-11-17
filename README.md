# LUMI AI Android APK build kit

This is an Android WebView wrapper for the existing live LUMI AI website:

https://lumi-ai-iy5t.onrender.com/

It does not copy API keys into the Android app. Gemini, Groq, Cloudflare image generation, PDF analysis, and chat history continue to run on the existing Render backend.

## Included Android support

- Full-screen WebView pointed at the live LUMI site
- JavaScript and DOM storage enabled for the existing web app
- PDF file picker for the website's `<input type="file" accept=".pdf">`
- DownloadManager integration for files downloaded from the site
- Android microphone/camera permission bridge for trusted LUMI-origin requests
- Browser back navigation
- Purple LUMI app theme and launcher icon

## Build the APK with GitHub Actions

1. Extract this ZIP.
2. In the `NOVA-AI` GitHub repository, upload the `android` folder and the `.github/workflows/build-lumi-apk.yml` file at the repository root. Keep the folder paths exactly as shown.
3. Commit the uploaded files.
4. Open the repository's **Actions** tab.
5. Select **Build LUMI AI APK** and open the latest successful run.
6. Download the artifact named **LUMI-AI-Android-APK**. It contains `app-debug.apk`.
7. Transfer `app-debug.apk` to an Android phone and install it. Android may ask to allow installation from that file manager/browser.

The workflow also runs automatically whenever files under `android/` or the workflow itself are pushed.

## Important notes

- The first APK is a debug-signed APK, suitable for testing and direct sharing. It is not a Play Store release-signed APK.
- The APK needs internet access because it loads the live Render website.
- Voice playback uses the Android WebView/browser's English speech engine. Availability and voice quality depend on the phone's installed speech services.
- Web Speech Recognition support varies by Android System WebView version and device. Typed chat is unaffected.
- PDF selection is supported by the native Android file picker.
- For a permanent public download, upload the APK to a GitHub Release or your LUMI STORE after the build succeeds. GitHub Actions artifacts expire after 30 days.
