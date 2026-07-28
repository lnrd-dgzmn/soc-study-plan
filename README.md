# SOC Analyst Study Plan — App Setup

Your study tracker is now a **PWA** (Progressive Web App). That means you can install it
straight to your phone like a normal app, *and* turn it into a real APK when you want one.

Files in this folder:
- `index.html` — the app
- `manifest.webmanifest` — app name, icon, colors
- `sw.js` — service worker (makes it work offline)
- `icons/` — app icons

You must serve these files over **HTTPS** for install/offline to work. Below is the free way.

---

## Step 1 — Put it online for free (GitHub Pages)

You'll already have a GitHub for your SOC journey, so use it:

1. Create a new public repo, e.g. `soc-study-plan`.
2. Upload everything in this folder (keep the `icons/` folder inside).
3. Go to **Settings → Pages**, set **Source: Deploy from a branch**, branch `main`, folder `/root`, Save.
4. After a minute you'll get a URL like `https://YOURNAME.github.io/soc-study-plan/`.

(Alternative: drag this folder onto **app.netlify.com/drop** for an instant HTTPS URL — no account needed to start.)

---

## Step 2a — Install it as an app (free, no APK)

On your Android phone, open the URL in **Chrome** → tap the **⋮ menu → Install app / Add to Home screen**.
It gets its own icon, opens full-screen, and works offline. For most people this is all you need.

## Step 2b — Turn it into a real APK (no coding)

1. Go to **https://www.pwabuilder.com** and paste your URL from Step 1.
2. Click **Package for stores → Android**.
3. Download the generated package (APK/AAB). PWABuilder signs it for you.
4. Copy the APK to your phone and open it (enable *Install unknown apps* for your file manager when prompted).

That's your installable APK. The same package can later go on the Google Play Store if you ever want.

---

## Optional — Build the APK locally (power route)

If you'd rather build it yourself with tools on your own machine (needs Node.js, JDK 17, and the Android SDK):

```bash
npm install -g @bubblewrap/cli
bubblewrap init --manifest https://YOURNAME.github.io/soc-study-plan/manifest.webmanifest
bubblewrap build
```

This outputs a signed `app-release-signed.apk`.

---

Note: your ticked-off progress is saved on each device separately (in the app's local storage),
so your phone app and your browser keep their own progress.
