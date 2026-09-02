# White-Label Learning Platform

**Production-grade Flutter architecture demo** for building multiple branded educational apps from a single codebase.

This repository showcases a clean, scalable system design used to power white-label learning applications — including dynamic configuration, modular features, offline-first architecture, and abstracted monetization.

> **Note**  
> This is a public architecture showcase with sanitized endpoints and mock configurations.  
> Core production engines, proprietary APIs, and live monetization keys remain in a private enterprise repository.

---

## Architecture Overview

The project follows a **Feature-First Clean Architecture** with strict separation between shared infrastructure and domain-specific feature modules.

```text
lib/
├── main.dart
└── src/
    ├── core/                       # Shared infrastructure
    │   ├── config/                 # White-label configuration engine
    │   ├── network/                # Dio client + secure gateway
    │   ├── theme/                  # Dynamic light/dark theme tokens
    │   ├── storage/                # Hive persistence layer
    │   └── monetization/           # RevenueCat + AdMob abstraction
    │
    └── features/                   # Independent feature modules
        ├── ai_tutor/               # Socratic AI chat & search
        ├── content/                # WordPress REST + course engine
        ├── quiz/                   # Adaptive quizzes & exam simulator
        ├── flashcards/             # Spaced repetition (SM-2)
        └── gamification/           # Streaks, XP, progression
```

---

## Tech Stack

| Layer              | Technology                          |
|--------------------|-------------------------------------|
| Framework          | Flutter (Dart ≥ 3.12)               |
| State Management   | Provider + `ChangeNotifier`         |
| Local Storage      | Hive / Hive CE                      |
| Networking         | Dio + custom interceptors           |
| Monetization       | RevenueCat + AdMob Mediation        |
| Backend            | Headless WordPress REST API         |
| Auth / Services    | Firebase                            |
| AI                 | Secure serverless AI gateway        |

---

## White-Label Configuration Engine

All branding, content sources, feature flags, and monetization keys are driven by a single `AppConfig` surface. Feature modules never hardcode brand-specific values.

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

  /// Demo configuration for public architecture showcase
  static const AppConfig demo = AppConfig(
    appId: 'com.demo.learningapp',
    appName: 'Demo Learn',
    wpHost: 'https://demo-cms.example.com',
    rootCategoryId: 101,
    revenueCatApiKey: 'goog_demo_key_placeholder',
    adMobBannerId: 'ca-app-pub-3940256099942544/6300978111', // Google test ad unit
    privacyPolicyUrl: 'https://example.com/privacy',
  );
}
```

This approach allows a single codebase to power multiple branded applications by simply swapping the configuration at build or runtime.

---

## Engineering Highlights

- **Zero-Secret AI Integration**  
  Client features communicate with a secure serverless gateway. API keys never ship inside the mobile binary.

- **Tiered Monetization Abstraction**  
  Clean separation between free-tier limits (AI quota, ad triggers) and premium entitlements managed through RevenueCat.

- **Offline-First Design**  
  Hive-powered persistence enables continuous quiz taking, flashcard review, and course access without network connectivity.

- **Adaptive Spaced Repetition**  
  Full SM-2 algorithm implementation with mistake ledger and optimized review scheduling.

- **Dynamic Theming**  
  Light/dark theme tokens driven by configuration, supporting brand-specific visual identity.

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/your-username/flutter-whitelabel-architecture-demo.git
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

| Principle                    | Implementation                                      |
|-----------------------------|-----------------------------------------------------|
| Feature isolation           | Each feature is a self-contained module             |
| Dependency direction        | Features depend on `core`, never the reverse        |
| Configuration over code     | Branding & flags live in `AppConfig`                |
| Testability                 | Providers and repositories are easily mockable      |
| Scalability                 | New brands or features require minimal changes      |

---

## Access & Contact

This repository is an open architectural sample intended for portfolio and hiring review.

For access to the full production codebase, private modules, or detailed technical discussion, feel free to reach out via GitHub or email.

---

**Built with Flutter · Clean Architecture · Production-minded design**
