# Bloom Learning Platform

> A modular, offline-first, feature-first Clean Architecture learning platform built with Flutter. This codebase is the shared technical core for a portfolio of subject-specific educational apps (economics, biology, sociology, astronomy, etc.) — this repository instance is subject-agnostic infrastructure; subject content is injected per app.

[![Flutter](https://img.shields.io/badge/Flutter-3.47.x-02569B?logo=flutter)](https://docs.flutter.dev/release/release-notes)
[![Dart](https://img.shields.io/badge/Dart-3.11.x-0175C2?logo=dart)](https://dart.dev)
[![State Management](https://img.shields.io/badge/State-Provider%20%2F%20ChangeNotifier-informational)]()
[![Local Storage](https://img.shields.io/badge/Storage-Hive-yellow)]()
[![Architecture](https://img.shields.io/badge/Architecture-Feature--First%20Clean%20Architecture-success)]()
[![License](https://img.shields.io/badge/license-Proprietary-lightgrey)]()

> **Note on scope:** This README documents structure and capabilities that are **verified from the repository's file layout**. Per the portfolio classification rules, only VERIFIED systems are described as shipped features; anything not directly evidenced by the codebase is intentionally omitted rather than assumed.

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. Architecture](#2-architecture)
- [3. Feature Modules](#3-feature-modules)
- [4. Tech Stack](#4-tech-stack)
- [5. State Management Conventions](#5-state-management-conventions)
- [6. Local Storage & Offline Strategy](#6-local-storage--offline-strategy)
- [7. Networking Layer](#7-networking-layer)
- [8. Security](#8-security)
- [9. Monetization](#9-monetization)
- [10. Notifications & Retention Engine](#10-notifications--retention-engine)
- [11. Project Structure](#11-project-structure)
- [12. Getting Started](#12-getting-started)
- [13. Build & Code Generation](#13-build--code-generation)
- [14. Testing Strategy](#14-testing-strategy)
- [15. Contributing Conventions](#15-contributing-conventions)

---

## 1. Overview

Bloom is the engineering core behind a family of 30+ subject-specific study apps that share one technical foundation and one learning philosophy:

```
LEARN → PRACTICE → MAKE MISTAKES → ANALYZE → IDENTIFY WEAKNESSES → ADAPT → REVIEW → IMPROVE
```

The platform combines structured lesson content, a quiz/practice engine, spaced-repetition flashcards, an automated mistake ledger, exam simulation, AI-assisted tutoring, and a full retention/gamification layer (streaks, XP, leaderboards, daily challenges) — all wired through a cache-first, offline-resilient data layer.

Each downstream app reuses this architecture while keeping its own subject content, branding, keywords, and store positioning independent.

---

## About (for recruiters / internship)

This is a production-style **learning platform shell**, not a demo todo app. It covers content delivery, AI study tools, monetization, retention, and social learning — designed so the same code can power different subjects and brands.

### What this project demonstrates

| Skill | Evidence in this codebase |
|-------|---------------------------|
| **Flutter architecture** | Feature-first modules under `lib/src/features/` + shared `lib/src/core/` |
| **State management** | Provider / `ChangeNotifier`, selective rebuilds |
| **White-label product engineering** | Single config surface (`AppUrl`) for 30+ apps |
| **Backend integration** | WordPress REST, Cloudflare gateway, Firebase |
| **Monetization** | Subscriptions, one-time IAPs, free-tier quotas, ads |
| **AI UX** | Subject-gated AI tutor, search, quiz generation (client talks to secured gateway — no API secrets in the app) |
| **Retention & growth** | Streaks, XP, leaderboards, friends, smart notifications |
| **Quality habits** | Tests under `test/`, theming via `Theme` / `AppColors`, offline/Hive storage |

### Role context

Built and maintained as part of **Bloom Code Studio** portfolio product work — shipping educational Android apps at scale from one codebase.

---

## Features

| Area | Capabilities |
|------|----------------|
| **Content** | WordPress courses, YouTube playlists, offline downloads |
| **Quiz** | Adaptive quizzes, exam simulator, ghost duels |
| **AI** | Socratic tutor, smart search, AI quiz generation |
| **Study tools** | Flashcards (SM-2), smart study plan, mistakes ledger, notebook |
| **Gamification** | Streaks, XP, daily goals, leaderboards, friends & challenges |
| **Monetization** | RevenueCat + AdMob mediation |
| **Retention** | Local notifications + FCM (premium skips retention locals) |
| **UI** | Light / Dark themes |

---

## White-label setup

Brand & environment config:

```
lib/src/core/utils/app_urls.dart
```

| Field | Purpose |
|-------|---------|
| `appId` / `appName` | Bundle id & display name |
| `assetFolder` / `playlistAssetFolder` | Quiz CDN + playlist stems |
| `wpHost` / `rootCategoryId` | WordPress content |
| RevenueCat + AdMob IDs | Monetization |
| `appStoreId` + legal URLs | Store / compliance |

Feature code reads product copy and endpoints from `AppUrl` — not hard-coded per subject.

---

## 11. Project Structure

```
lib/
├── firebase_options.dart
├── hive_registrar.g.dart
├── model/                      # legacy/shared models (api, hive, ai) — pre-migration
│   ├── api/
│   ├── hive/
│   └── ai/
├── in-app purchase/            # legacy IAP module (pre feature-first migration)
├── utils/                      # legacy top-level utils
└── src/
    ├── core/
    │   ├── monetization/
    │   ├── network/
    │   ├── security/
    │   ├── services/
    │   │   └── notifications/
    │   ├── storage/
    │   ├── theme/
    │   ├── utils/
    │   └── widgets/
    └── features/
        ├── ai/ ai_tutor/ ai_history/
        ├── analytics/
        ├── cosmetics/
        ├── daily_goals/
        ├── discord/
        ├── educational_content/
        ├── engagement/
        ├── exam_simulator/
        ├── feedback/
        ├── flashcards/
        ├── friends/
        ├── gamification/
        ├── leaderboards/
        ├── learning/
        ├── mastery/
        ├── mistakes/
        ├── monetization/
        ├── notebook/
        ├── notifications/
        ├── onboarding/
        ├── quiz/ quiz_engine/
        ├── retention/
        ├── smart_search/
        ├── smart_study_plan/
        ├── streak/
        ├── video_companion/
        └── visual_learning/
```

> `lib/model/`, `lib/in-app purchase/`, and `lib/utils/` sit outside `lib/src/` — these are **legacy pre-migration locations**. New work should land inside `lib/src/{core|features}/...`; treat the top-level folders as migration debt, not a pattern to replicate. (Also: the `in-app purchase/` directory name contains a space, which is invalid for import URIs on some tooling/platforms — flag for rename to `in_app_purchase/` during the next migration pass.)

---

## 12. Getting Started

### Prerequisites

- Flutter SDK **3.47.x** (stable channel)
- Dart **3.11.x** (bundled with the above Flutter SDK)
- A configured Firebase project (`firebase_options.dart` must match your project — regenerate via FlutterFire CLI if forking)
- Android Studio / Xcode for platform toolchains, VS Code or IntelliJ for day-to-day development

### Setup

```bash
# 1. Install dependencies
flutter pub get

# 2. Regenerate Firebase configuration for your project (if forking)
dart pub global activate flutterfire_cli
flutterfire configure

# 3. Generate Hive adapters & any other build_runner outputs
dart run build_runner build --delete-conflicting-outputs

# 4. Run
flutter run
```

---

## 13. Build & Code Generation

Any file ending in `.g.dart` (Hive adapters: `streak_model.g.dart`, `bookmark.g.dart`, `flashcard_record.g.dart`, `mistake_record.g.dart`, `notification_prefs.g.dart`, `completed_lessons.g.dart`, `notebook_entry_record.g.dart`, plus `hive_registrar.g.dart`) is **generated, not hand-edited**.

```bash
# One-off generation
dart run build_runner build --delete-conflicting-outputs

# Watch mode during active model changes
dart run build_runner watch --delete-conflicting-outputs
```

Whenever a Hive-annotated entity changes shape, regenerate before running — stale adapters are a common source of runtime `HiveError`s that won't surface at compile time.

---

## 14. Testing Strategy

The repository's business logic is concentrated in pure Dart domain services — these are the highest-leverage unit test targets:

| Tier | Behavior |
|------|----------|
| **Free** | Daily/weekly caps (AI, exams, lessons, study plan); ads on |
| **Premium** | Unlimited study/AI tools, ad-free, streak freezes & cosmetics |

IAP prices come from the store via RevenueCat — amounts are never hard-coded.

---

## 15. Contributing Conventions

- **Strict typing** — avoid `dynamic` and the `!` bang operator; prefer sealed classes/`Either`-style result types (this repo already models this via `ApiResult<T>`) over throwing across layers.
- **`const` everywhere possible** — constructors, widgets, and literals, to reduce rebuild cost.
- **Respect the Clean Architecture boundary** — presentation never imports a data-layer implementation directly; it depends on the domain contract.
- **New features are feature-first** — create `domain/`, `data/`, `presentation/` under `lib/src/features/<feature_name>/`, not under the legacy top-level folders.
- **Dispose everything you subscribe to** — providers, controllers, and streams must clean up in `dispose()`.
- **Offline-aware by default** — any new network call should go through the existing cache-first pattern (§6) unless there's a specific reason to bypass it (state that reason in the PR).
- **No subject-specific content in shared/core code** — subject content belongs in app-level configuration, never hardcoded into `lib/src/core/` or shared feature logic, to preserve reusability across the portfolio.
