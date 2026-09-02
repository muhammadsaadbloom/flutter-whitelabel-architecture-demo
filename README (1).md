# Bloom — Flutter Learning Platform Architecture

**Production-scale Flutter architecture case study** for a multi-feature, white-label educational app: adaptive learning, gamification, social features, and tiered monetization on a single codebase.

> **Note on this repository**
> This is a public architectural case study. Endpoints, API keys, `RevenueCat`/`AdMob` identifiers, and `firebase_options.dart` have been replaced with placeholders. If you're evaluating this as a fork/template, do **not** ship it without regenerating your own Firebase project, RevenueCat entitlements, and AdMob unit IDs.

---

## Architecture Overview

**Feature-First Clean Architecture** — each feature is a self-contained module (`domain` / `data` / `presentation`), depending only on `core`, never the reverse.

```text
lib/
├── main.dart
├── firebase_options.dart
├── model/                          # Shared Hive + API DTOs
├── hive_registrar.g.dart
├── in-app purchase/                # Platform IAP layer (store <-> RevenueCat bridge)
└── src/
    ├── core/
    │   ├── network/                 # Dio client, gateway auth, retry/backoff, SSL pinning
    │   ├── security/                # App Check, secure token store, log sanitizer, input validation
    │   ├── storage/                 # Hive box management
    │   ├── theme/                   # Design tokens, responsive layout, dynamic theming
    │   ├── monetization/            # Entitlements, paywall, ads, spin wheel, offer engine
    │   ├── services/                # Notifications, retention, sync, boot/launch coordination
    │   ├── providers/                # App-wide state (user session, etc.)
    │   ├── utils/                    # Device capability/identity, app upgrader, offline guard
    │   └── widgets/                  # Shared UI primitives
    │
    └── features/
        ├── ai/                       # AI gateway, token quota, JSON repair, exceptions
        ├── ai_tutor/                  # Socratic tutoring flow
        ├── ai_history/                # AI interaction history
        ├── learning/                  # Lesson reading, progress tracking, micro-checks
        ├── educational_content/       # Curriculum catalog & skill-tree progress
        ├── visual_learning/            # Concept mapping & interactive playground
        ├── video_companion/            # Video/playlist content + unlock policy
        ├── quiz_engine/                # Core quiz runtime, validation, sections
        ├── quiz/                       # First-quiz onboarding flow
        ├── exam_simulator/             # Adaptive exam engine, difficulty estimation, review
        ├── flashcards/                  # SM-2 spaced repetition scheduler
        ├── notebook/                    # Smart notebook (source-linked notes)
        ├── mistakes/                    # Mistake journal & repository
        ├── mastery/                     # Category mastery calculation
        ├── analytics/                    # Exam readiness scoring, performance tracking
        ├── smart_search/                  # In-app search
        ├── smart_study_plan/               # Generated study plans & task launcher
        ├── daily_goals/                     # Daily goal tracking
        ├── streak/                           # Streak state, freeze/recovery logic
        ├── gamification/
        │   ├── xp/                            # XP, levels, boosts
        │   ├── achievements/                   # Unlock conditions & popups
        │   ├── daily_challenges/                # Daily challenge catalog
        │   └── daily_bonus/                      # Daily bonus calendar
        ├── leaderboards/                          # League tiers, promotion zones, podium
        ├── cosmetics/                               # Cosmetic shop/items
        ├── friends/                                  # Friend graph, challenges, privacy
        ├── discord/                                   # Discord roles/events integration
        ├── engagement/
        │   ├── retention_dashboard/                    # Retention metrics UI
        │   ├── personalized_recommendations/            # Recommendation engine
        │   ├── daily_fact/ · daily_quote/                # Daily content widgets
        │   └── learning/                                  # Daily review screen
        ├── retention/                                       # Progress insights, weekly challenges, boosters
        ├── notifications/                                     # In-app banners, settings
        ├── onboarding/                                          # Age gate, country picker, name input
        ├── feedback/                                              # Bug reports, feature requests, ratings
        └── monetization/                                           # IAP store UI section
```

---

## Tech Stack

| Layer              | Technology                                              |
|--------------------|----------------------------------------------------------|
| Framework          | Flutter (Dart ≥ 3.12, sealed classes / patterns)         |
| State Management   | `Provider` + `ChangeNotifier`                            |
| Local Storage      | Hive / Hive CE (offline-first persistence)                |
| Networking         | Dio — custom interceptors for auth, retry/backoff, gateway routing |
| Security           | SSL pinning, Firebase App Check, secure token storage, log sanitization |
| Monetization       | RevenueCat (subscriptions) + platform IAP bridge + AdMob mediation |
| Backend            | Headless CMS via REST + secure serverless AI gateway       |
| Auth / Infra       | Firebase (Auth, Crashlytics, Cloud Messaging)               |
| AI                 | Server-side gateway pattern — no AI provider keys ship on-device |

---

## Engineering Highlights

- **Zero-Secret AI Integration** — AI features route through a serverless gateway; no provider keys embedded in the client. Includes daily quota tracking and JSON-repair for malformed model output.
- **Tiered Monetization Engine** — Free-tier limits (AI quota, quiz retries, notebook access, ad triggers), reward mechanics (streak multipliers, spin wheel, daily bonus), and premium entitlement gating, all centralized through a single entitlement cache.
- **Retention & Notification System** — A/B-tested, personalized push notifications with per-trigger logic (streak risk, friend activity, content drops, re-engagement) and an engagement guard to prevent notification fatigue.
- **Offline-First Design** — Hive-backed persistence for quizzes, flashcards, streaks, and study plans; sync services reconcile state once connectivity returns.
- **Adaptive Learning** — SM-2 spaced repetition, adaptive exam difficulty estimation, and mastery calculation feed a generated study plan.
- **Social Layer** — Friend graph with privacy controls, peer challenges, and Discord role/event integration.
- **Defense in Depth** — SSL pinning, Firebase App Check, secure token storage, and input validation live in `core/security`, isolated from feature code.

---

## Getting Started

### 1. Clone and configure

```bash
git clone https://github.com/your-username/bloom-flutter-architecture.git
cd bloom-flutter-architecture
```

Replace `lib/firebase_options.dart` with your own `flutterfire configure` output, and set your own RevenueCat/AdMob identifiers in the monetization config before running.

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

### 5. Run

```bash
flutter run
```

---

## Project Structure Philosophy

| Principle                | Implementation                                         |
|---------------------------|----------------------------------------------------------|
| Feature isolation          | Each feature owns its `domain`/`data`/`presentation` layers |
| Dependency direction        | Features depend on `core`; `core` never depends on features |
| Configuration over code      | Branding, flags, and entitlements are externally driven |
| Testability                   | Providers/repositories are constructor-injected and mockable |
| Scalability                    | New features or brands require no changes to existing modules |

---

## License & Access

This repository is shared for portfolio and technical review purposes. See [`LICENSE`](./LICENSE) for terms.

For questions about the architecture or production deployment details, open an issue or reach out via the contact info on my GitHub profile.

---

**Built with Flutter · Clean Architecture · Offline-first · Production-minded design**
