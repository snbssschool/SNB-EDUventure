<div align="center">

# SNB EDUventure

### The official SNB Senior Secondary School app.


[![version](https://img.shields.io/badge/version-v2026.404.5-blue)](https://github.com/snbssschool/SNB-EDUventure/releases/latest)
[![android](https://img.shields.io/badge/Android-API%2024%2B-3DDC84?logo=android&logoColor=white)](https://github.com/snbssschool/SNB-EDUventure/releases/latest)
[![flutter](https://img.shields.io/badge/Flutter-3.47-02569B?logo=flutter&logoColor=white)](https://flutter.dev)
[![telemetry](https://img.shields.io/badge/telemetry-zero-red)](https://github.com/snbssschool/SNB-EDUventure/blob/main/README.md#-privacy-guarantee)
[![rights](https://img.shields.io/badge/©-SNB_Senior_Secondary_School-lightgrey)](https://snbhojai.com)

[⬇️ Download the APK](https://github.com/snbssschool/SNB-EDUventure/releases/latest) &nbsp;·&nbsp; [Privacy promise](#-privacy-guarantee) &nbsp;·&nbsp; [What's new](RELEASE_NOTES.md)

</div>

---

## 📸 Screenshots

<!-- Drop images into docs/screenshots/ and uncomment:
<div align="center">
  <img src="docs/screenshots/menu.png" width="270" alt="9-tile menu" />
  <img src="docs/screenshots/webview.png" width="270" alt="Immersive webview" />
  <img src="docs/screenshots/settings.png" width="270" alt="App Settings" />
</div>
-->

*Coming soon — splash, menu, webview and settings captures.*

---

## ✨ Highlights

| | | |
|---|---|---|
| 🎬 **Animated splash** with prewarmed webview | 🧭 **9-tile menu** — Dashboard, Homepage, Noticeboard, Course, Visit Us, Teachers, Contact, About Us + native App Settings | 🌐 **Immersive webview** of snbhojai.com — no app bar, floating home button |
| 🔐 **App lock** — PIN, pattern, password or fingerprint | 👆 **One-placement unlock** — a cancelled prompt is never called "not recognised" | 🧠 **Argon2id** credential storage (64 MiB, memory-hard) |
| 🌗 **Light / Dark** + dark-web-pages toggle | 📵 **Screenshot blocking** (Settings → Screen capture, default ON) | 🔄 **Pull-to-refresh**, only at page top |
| 🔗 External domains ask first, then open in browser | 📞 `mailto:` / `tel:` / `sms:` jump to system apps | ▶️ YouTube embeds play **in-app** |
| ⬇️ Downloads confirm first, land in Downloads | 📡 **Offline screen** with retry | 🚪 Double-press-to-exit (toggleable) |
| 🧹 Site header/footer hiding, list never erased | 📜 Native **privacy-policy reader**, fetched fresh | 🔔 **Notifications** for `/all-notification` | 🔄 **In-app updater** from GitHub Releases |

---

## 🔒 Privacy guarantee

- **Zero telemetry. Zero analytics. Zero trackers. Zero ads. Zero crash reporters. Zero Play Services.**
- Chromium **Safe Browsing is permanently OFF** — visited URLs never leave the phone.
- Tracker hosts are denied in `shouldInterceptRequest`.
- `allowBackup="false"` — no cloud backup of app data.
- All preferences stay in on-device `SharedPreferences`.
- The app makes exactly **two kinds** of network calls, nothing else:
  1. **snbhojai.com** itself (the school site you asked to see).
  2. **One anonymous GitHub Releases check per session** (at most one per 6 hours across restarts) — an identifier-free `GET`, no account, no device info.

---

## 🛡️ Security

| Area | Posture |
|---|---|
| App-lock KDF | **Argon2id** `m=65536 KiB, t=1, p=1` (`argon2id$m=…$<hex>`); legacy iterated-SHA-256 records auto-upgrade after the first **correct** unlock |
| Biometrics | One placement grants access; cancel/supersede → silent retry, only genuine lockout earns *"Fingerprint not recognised"* |
| Signatures | **v1 ✅ v2 ✅ v3 ✅ v4 ✅** |
| Signing cert | Self-signed, `CN=SNB EDUventure`, valid **until 18 Jul 9999** |
| Cert SHA-256 | `2F:7A:97:0B:1A:E9:81:AD:B3:DB:4E:DE:48:A4:26:C7:22:67:71:F4:17:C0:25:A5:40:1D:C6:28:89:88:E3:37` |
| Capture | `FLAG_SECURE` (screenshots / recordings / recents preview blanked), toggle in Settings |
| Installs | `REQUEST_INSTALL_PACKAGES` declared; runtime grant only when installing an update |
| WebView | Server-trust mismatch → load cancelled; no cert pinning beyond that; zoom always enabled |

---

## 🪪 App identity

| Field | Value |
|---|---|
| Package | `com.snb.pkm.the.royal.bengal.tiger` |
| Version | `v2026.404.5` (versionCode `405`) |
| Label | `SNB EDUventure` |
| minSdk / targetSdk | `24` / `36` (compileSdk `37`) |
| Size | ~56.5 MB release APK |
| Status bar | Always visible (black in light, white in dark); nav bar hidden; edge-to-edge |

---

## 🧰 Tech stack

| Layer | Choice |
|---|---|
| Framework | Flutter **3.47.5** / Dart **3.13.4**, Material 3 |
| State | `flutter_riverpod` |
| Webview | `flutter_inappwebview` 6.1.5 (persistent, prewarmed) |
| Lock | `local_auth` + `cryptography` (Argon2id) + `crypto` (legacy migration) |
| Settings / prefs | `shared_preferences` |
| Connectivity | `connectivity_plus` |
| Permissions / intents | `permission_handler`, `url_launcher` |
| Update checks | `http` (anonymous GitHub API GET only) |
| Policy reader | `html` (parsed natively, never rendered in a WebView) |
| Native bridge | `MethodChannel("snb_eduventure/io")` + 2 Kotlin files |

---

## 📲 Install / upgrading

1. Download the APK from [Releases](https://github.com/snbssschool/SNB-EDUventure/releases/latest).
2. Open it on your phone → allow *Install unknown apps* when asked → Install.
3. The in-app updater will offer future versions automatically.

> ⚠️ **Coming from the old build?** The application id changed
> (`com.snb.pkm.optimised.by.vibes` → `com.snb.pkm.the.royal.bengal.tiger`)
> **and** the signing key was renewed. There is no in-place upgrade path:
> **uninstall the old app, then install the new APK.** Your lock and settings do not transfer.

---

## 🔨 Build from source

```powershell
flutter pub get
flutter analyze
flutter test
flutter build apk --release
# output: build\app\outputs\flutter-apk\app-release.apk
```

> 🔑 **Never commit signing material.** `android/key.properties`,
> `android/app/upload-keystore.jks` (and any `*.backup-*.jks`) must stay
> out of git. They are local-only by design.

---

## 🏫 Credits

Built for **SNB Senior Secondary School** — [snbhojai.com](https://snbhojai.com).

© SNB Senior Secondary School. All rights reserved. Source is visible for transparency; no open-source license is granted.
