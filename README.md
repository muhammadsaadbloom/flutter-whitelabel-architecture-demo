# Flutter White-Label Learning Platform — Architecture Showcase

[![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?logo=flutter&logoColor=white)](https://flutter.dev)
[![Dart](https://img.shields.io/badge/Dart-3.x-0175C2?logo=dart&logoColor=white)](https://dart.dev)
[![Architecture](https://img.shields.io/badge/Architecture-Clean%20%2F%20Feature--First-4CAF50)](#architecture-overview)
[![License](https://img.shields.io/badge/License-MIT-informational)](./LICENSE)

**A production-grade Flutter architecture for shipping multiple branded educational apps from a single codebase.**

One engine. Any brand. Swap a config, not the code — new white-label apps launch without touching feature logic.

> **About this repository**
> This is a public architecture showcase with sanitized endpoints, mock API keys, and placeholder branding. The proprietary content pipeline, live monetization credentials, and several production-only modules are kept in a private repository. What's here is real, working architecture — not pseudocode.

---

## Why This Matters

**For business owners** — this is the engineering pattern behind running a portfolio of branded apps (different names, colors, content, store listings) without maintaining N separate codebases. New brand = new config file, not a new build.

**For recruiters / technical reviewers** — this repo demonstrates Clean Architecture discipline at production scale: strict feature isolation, offline-first data, secure API boundaries, and a monetization layer that's fully decoupled from learning logic. It's meant to be read, not just run.

---

## Architecture Overview

**Feature-First Clean Architecture** — every feature owns its `domain` / `data` / `presentation` layers. Features depend on `core`; `core` never depends on a feature.

```text
lib/
├── main.dart
├── firebase_options.dart          # Placeholder — regenerate per brand
└── src/
    ├── core/                       # Shared infrastructure — brand-agnostic
    │   ├── config/                  # White-label configuration engine
    │   ├── network/                 # Dio client, gateway auth, retry/backoff, SSL pinning
    │   ├── security/                # App Check, secure token storage, input validation
    │   ├── storage/                  # Hive persistence layer
    │   ├── theme/                    # Design tokens — brand-driven light/dark theming
    │   └── monetization/               # RevenueCat + AdMob abstraction, entitlement gating
    │
    └── features/                    # Independent, swappable feature modules
        ├── ai_tutor/                  # Socratic AI chat & search
        ├── content/                    # Headless CMS content engine
        ├── quiz_engine/                  # Adaptive quizzes & exam simulator
        ├── flashcards/                     # SM-2 spaced repetition
        └── gamification/                    # Streaks, XP, achievements, progression
```

---

## White-Label Configuration Engine

Branding, content sources, feature flags, and monetization keys are driven by a single `AppConfig` surface. Feature modules never hardcode brand-specific values — this is what makes "one codebase, many apps" possible.

```dart
// lib/src/core/config/app_config.dart

class AppConfig {
  final String appId;
  final String appName;
  final String wpHost;
  final int rootCategoryId;
  final String revenueCatApiKey;
  final String adMobBannerId;
  final String privacyPolicyUrl;

  const AppConfig({
    required this.appId,
    required this.appName,
    required this.wpHost,
    required this.rootCategoryId,
    required this.revenueCatApiKey,
    required this.adMobBannerId,
    required this.privacyPolicyUrl,
  });

  /// Demo configuration — public showcase only
  static const AppConfig demo = AppConfig(
    appId: 'com.demo.learningapp',
    appName: 'Demo Learn',
    wpHost: 'https://demo-cms.example.com',
    rootCategoryId: 101,
    revenueCatApiKey: 'goog_demo_key_placeholder',
    adMobBannerId: 'ca-app-pub-3940256099942544/6300978111', // Google test unit
    privacyPolicyUrl: 'https://example.com/privacy',
  );
}
```

Launching a new branded app is a matter of authoring a new `AppConfig` instance — no feature code changes, no forked repo.

---

## Tech Stack

| Layer              | Technology                          |
|--------------------|--------------------------------------|
| Framework          | Flutter (Dart ≥ 3.x)                  |
| State Management   | `Provider` + `ChangeNotifier`          |
| Local Storage      | Hive / Hive CE — offline-first          |
| Networking         | Dio + custom interceptors (auth, retry, SSL pinning) |
| Monetization       | RevenueCat + AdMob mediation              |
| Backend            | Headless CMS via REST                       |
| Auth / Infra       | Firebase (Auth, Crashlytics, Messaging)      |
| AI                 | Secure serverless gateway — no provider keys on-device |

---

## Engineering Highlights

- **Zero-Secret AI Integration** — AI features route through a serverless gateway; API keys never ship inside the client binary.
- **Tiered Monetization, Fully Decoupled** — free-tier limits and premium entitlements are resolved through a single gate, independent of any feature's business logic.
- **Offline-First by Default** — Hive-backed persistence keeps quizzes, flashcards, and course progress usable with zero connectivity.
- **Adaptive Spaced Repetition** — full SM-2 scheduling with a mistake ledger driving review priority.
- **Secure by Construction** — SSL pinning, Firebase App Check, and encrypted local token storage live in `core/security`, isolated from every feature.
- **Config-Driven Branding** — theming, copy, store metadata, and monetization identifiers are runtime/build-time config, not scattered constants.

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/muhammadsaadbloom/flutter-whitelabel-architecture-demo.git
cd flutter-whitelabel-architecture-demo
```

### 2. Install dependencies

```bash
flutter pub get
```

### 3. Generate Hive adapters

```bash
dart run build_runner build --delete-conflicting-outputs
```

### 4. Analyze & test

```bash
flutter analyze
flutter test
```

### 5. Run the demo

```bash
flutter run
```

---

## Project Structure Philosophy

| Principle                | Implementation                                      |
|---------------------------|-------------------------------------------------------|
| Feature isolation          | Each feature is a self-contained module               |
| Dependency direction        | Features depend on `core`, never the reverse           |
| Configuration over code      | Branding & flags live in `AppConfig`, not in feature code |
| Testability                   | Providers and repositories are constructor-injected and mockable |
| Scalability                    | New brands or features require minimal, isolated changes |

---

## About the Author

Built and maintained by **Muhammad Saad** — Flutter engineer focused on production-grade mobile architecture, offline-first systems, and scalable white-label platforms.

- GitHub: [@muhammadsaadbloom](https://github.com/muhammadsaadbloom)
- Open to full-time roles, contract work, and technical discussions about this architecture.

---

## License

Released under the [MIT License](./LICENSE) — free to use as a reference or starting point for your own architecture.

---

**Built with Flutter · Clean Architecture · Offline-First · Production-Minded Design**
