# SNB-EDUventure
## Privacy Guarantee
- Zero telemetry, zero analytics, zero trackers.

Project Highlights
Modern Android 16 (API 36) Build Architecture: Configured with AGP 9.0.1, Gradle 9.1.0, JDK 17, and Kotlin 2.2.10 via Gradle Version Catalog (libs.versions.toml). Explicitly opted out of AGP 9.0 built-in Kotlin in favor of the traditional org.jetbrains.kotlin.android plugin to prevent toolchain mismatches.

Strict Zero-Telemetry Privacy: 
Contains zero analytics, zero ad SDKs, zero crash reporters, and zero Google Play Services dependencies. Chromium Safe Browsing is permanently disabled via WebSettingsCompat.setSafeBrowsingEnabled(webView.settings, false) to prevent visited URLs from being transmitted to external servers.

Local-Only Heuristic Root Detection: Utilizes com.scottyab:rootbeer-lib:0.1.2 (Apache 2.0) for 100% offline heuristic analysis at application launch. If tampering or su binaries are detected, the app presents a non-bypassable MaterialAlertDialogBuilder alert and exits via finishAndRemoveTask() before the WebView is ever initialized.

Edge-to-Edge Layout & Dynamic Status Bar Scrim: 
Compliant with Android 15/16 (API 35+) where Window.setStatusBarColor() is deprecated and ignored. Features a custom StatusBarScrimView pinned to the status bar window insets that animates color transitions (ValueAnimator + ArgbEvaluator) using dynamically evaluated CSS theme colors (meta[name=theme-color] or computed body background), automatically switches status bar icon contrast using luminance calculations, and modulates shade on vertical scroll.

First-Launch Theme Choice & Algorithmic Darkening: 
Non-dismissible first-launch dialog offering Light and Dark themes stored in local SharedPreferences. In Dark Mode, an optional "Darken web pages too" toggle activates WebSettingsCompat.setAlgorithmicDarkeningAllowed for pages lacking native CSS dark themes.

Hand-Rolled 500 MB LRU Disk Cache: 
Avoids the archived JakeWharton/DiskLruCache library in favor of a thread-safe, self-contained LRU cache in context.cacheDir. Intercepts image requests (.jpg, .png, .webp, .svg, .gif) in WebViewClient.shouldInterceptRequest and respects Cache-Control / ETag headers.

Embedded Video Fullscreen: 
Implements WebChromeClient.onShowCustomView and onHideCustomView to lock orientation to landscape during HTML5 and YouTube video playback, seamlessly wired into the modern OnBackPressedCallback.

Predictive Back Navigation (API 36): 
Implements OnBackPressedCallback via onBackPressedDispatcher with android:enableOnBackInvokedCallback="true", routing back gestures from fullscreen video exit to WebView history, and prompting with a randomized exit confirmation message from the 59-item pool before closing.

Animated Loading & Offline Overlays: 
Custom layered-motion overlays featuring the exact pool of 100 witty loading messages on every page load, and an offline overlay featuring a breathing disconnected cloud, persistent "You are offline" title, and a retry mechanism with local assets served via WebViewAssetLoader.
