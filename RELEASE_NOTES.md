# 2026.404.5 — hardened build: Argon2id lock, one-touch unlock, capture blocking

> 📋 This file is the release body for tag `2026.404.5`. Paste it into the
> GitHub release notes (it is also what the in-app update dialog shows).

## ⚠️ Install note — read first

- New application id: `com.snb.pkm.the.royal.bengal.tiger`
- New signing key (old cert retired).
- **If you have the previous build installed: uninstall it first, then install this APK.** No in-place upgrade is possible. Lock and settings do not transfer.

## 🆕 New in this build

- 🔐 **Argon2id credential storage** (`m=65536 KiB, t=1, p=1`) — memory-hard instead of iterated SHA-256. Old hashes upgrade automatically after the first **correct** unlock, never after a wrong guess.
- 👆 **Fingerprint unlock fixed to one placement** — a cancelled or superseded prompt is never reported as *"Fingerprint not recognised"*. Only a genuine lockout earns that line.
- 📵 **Block screenshots & screen recording** — new toggle in Settings → Screen capture, **default ON** (applies before the first frame).
- 🔄 **Smarter updater** — *Update now* is offered only when the release actually carries an APK; otherwise the dialog offers *Open release page*. Automatic checks run at most once per **6 hours** (the manual row always goes).
- 🪪 Package renamed to `com.snb.pkm.the.royal.bengal.tiger`.
- 🔏 Re-signed: cert valid **until 18 Jul 9999**.
- 🔢 Version display is now `v2026.404.5`.

## ✨ What this app is

The official SNB Senior Secondary School app with app lock (PIN / pattern / password / fingerprint), light + dark themes, pull-to-refresh, offline screen, downloads, notifications, and an in-app updater. **No telemetry.**

## 🔒 Privacy

Zero telemetry, zero analytics, zero trackers, zero ads. The only network calls are the school site itself and one anonymous GitHub release check per session.

## 📦 Verify your download

| Check | Value |
|---|---|
| Package | `com.snb.pkm.the.royal.bengal.tiger` |
| versionName / versionCode | `v2026.404.5` / `405` |
| Signatures | v1 ✅ v2 ✅ v3 ✅ v4 ✅ |
| APK SHA-256 | `66a9c2c8786ce91fbfe11038003bc36176aad6bfb421dc6a8e0ab1015ec6ba5b` |
| Signing-cert SHA-256 | `2F:7A:97:0B:1A:E9:81:AD:B3:DB:4E:DE:48:A4:26:C7:22:67:71:F4:17:C0:25:A5:40:1D:C6:28:89:88:E3:37` |

⬇️ **Asset:** `SNB-EDUventure-2026.404.5-release.apk` (~56.5 MB)
