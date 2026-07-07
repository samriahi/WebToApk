# Android WebView App Builder

Turn any website into a standalone Android APK — no coding, no Android Studio, no local build tools. Just fill in a form on GitHub Actions and download the APK a few minutes later.

This project wraps a website inside a native Android WebView shell and uses **GitHub Actions** to build the APK entirely in the cloud.

---

## How It Works

1. You provide an **app name** and a **website URL** using GitHub's built-in "Run workflow" form.
2. GitHub Actions automatically:
   - Updates the app's name and target URL
   - Builds a debug APK using Gradle
   - Uploads the finished APK as a downloadable artifact
3. You download the APK and install it on your Android phone.

No local Android SDK, no Kotlin knowledge, and no manual editing required.

---

## Requirements

- A GitHub account
- An Android phone (or emulator) to install the resulting APK
- That's it — everything else runs in GitHub's cloud

---

## Step-by-Step Usage Guide

### 1. Get Your Own Copy of This Repo
Click the **Fork** button (top-right of this repository page) to create your own copy under your GitHub account.

### 2. Open the Actions Tab
On your forked repository, click the **Actions** tab near the top of the page.

If prompted with a message about workflows being disabled on forks, click **"I understand my workflows, go ahead and enable them"**.

### 3. Select the Build Workflow
In the left sidebar, click **Build APK**.

### 4. Run the Workflow
1. Click the **Run workflow** dropdown button (top-right of the workflow list).
2. Fill in the form:
   - **App Name** — the name you want displayed under the app icon (e.g. `My Cool App`)
   - **Website URL** — the full URL of the website you want to wrap (e.g. `https://example.com`)
3. Click the green **Run workflow** button to confirm.

### 5. Wait for the Build
- A new run will appear at the top of the list with a yellow dot (in progress).
- Click into it to watch live build logs if you're curious.
- After 2–5 minutes, the dot turns into a green checkmark ✅ (success) or a red ✗ (failed).

### 6. Download the APK
1. Click on the completed workflow run.
2. Scroll down to the **Artifacts** section at the bottom of the page.
3. Click **app-debug** to download a `.zip` file.
4. Unzip it — inside you'll find `app-debug.apk`.

### 7. Install on Your Phone
1. Transfer the APK to your Android phone (via Telegram, email, USB cable, etc.).
2. Open the APK file on your phone.
3. If prompted, allow installation from this source:
   **Settings → Security → Install unknown apps** → enable for the app you used to open the file (e.g. Files, Telegram).
4. Tap **Install**.

You now have a native Android app that opens your website inside a WebView! 🎉

---

## Building Again With a Different Site

You don't need to fork again. Just repeat **steps 3–7** with a new App Name and Website URL — each run produces its own APK without affecting your repo's files permanently (unless triggered by a direct push to `main`).

---

## Notes & Limitations

- The generated app requires an internet connection to load the website (it does not download the site for offline use).
- The website must be **publicly accessible** (e.g. deployed on Vercel, Netlify, or your own server) — `localhost` URLs won't work since the build happens on GitHub's servers.
- This produces a **debug** APK, suitable for personal use and testing. For publishing to the Google Play Store, additional signing and release configuration is required.

---

## Troubleshooting

| Problem | Likely Cause |
|---|---|
| Workflow doesn't appear under Actions | Workflows need to be manually enabled on forks — see Step 2 |
| Build fails (red ✗) | Check the build log for errors; often caused by special characters (`&`, `"`) in the App Name or URL |
| APK won't install | Make sure "Install unknown apps" is allowed for the app you used to open the file |
| App opens but shows a blank/error page | Double-check the Website URL is correct and publicly reachable |

---

## Credits

Based on the [Android-WebView-App-Template](https://github.com/devSp741/Android-WebView-App-Template) project, extended with a GitHub Actions workflow for one-click, no-code APK generation.