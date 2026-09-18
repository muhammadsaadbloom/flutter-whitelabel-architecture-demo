# Bloom Learning Platform

## Production Flutter Architecture for a Portfolio of Subject-Specific Learning Apps

Bloom Learning Platform is the shared Flutter engineering foundation behind a portfolio of subject-specific educational applications developed and maintained by Bloom Code Studio.

The platform is designed around a practical product requirement: build, maintain, and release multiple learning applications without repeatedly rebuilding the same application architecture, networking layer, study systems, local storage, monetization infrastructure, and engagement features.

Instead of maintaining separate codebases for every subject, the platform separates reusable product functionality from subject-specific content, branding, configuration, and store positioning.

The result is a feature-first Flutter architecture that can support a portfolio of educational applications while keeping shared engineering logic centralized and maintainable.

**Role:** Founder and Flutter Developer  
**Development:** Independently designed, developed, maintained, and published  
**Primary Technology:** Flutter / Dart  
**Architecture:** Clean Architecture + Feature-First + MVVM-style presentation  
**State Management:** Provider / ChangeNotifier  
**Published Portfolio:** 50+ production Android applications  
**Flagship Portfolio Result:** 1M+ Google Play downloads on a flagship educational application  
**Repository Purpose:** Engineering case study and portfolio demonstration

---

# At a Glance

- 50+ production Android applications published on Google Play
- 1M+ downloads on a flagship educational application
- 3+ years of hands-on Flutter development
- Independently responsible for application development and production maintenance
- Feature-first Clean Architecture
- Provider / ChangeNotifier with MVVM-style presentation
- REST APIs and Dio
- WordPress REST API integration
- Firebase services
- Hive CE and offline-first data handling
- AI-powered learning features
- RevenueCat and AdMob
- Google Play production releases
- Debugging, maintenance, and iterative product development

This repository focuses on the engineering behind the applications rather than presenting the portfolio only as a list of published apps.

---


---

## Table of Contents

- [Project Overview](#project-overview)
- [The Engineering Problem](#the-engineering-problem)
- [The Solution](#the-solution)
- [Portfolio Scale](#portfolio-scale)
- [My Role and Ownership](#my-role-and-ownership)
- [Architecture](#architecture)
- [Why Feature-First Clean Architecture](#why-feature-first-clean-architecture)
- [White-Label Configuration](#white-label-configuration)
- [Application Flow](#application-flow)
- [Feature Modules](#feature-modules)
- [Learning System](#learning-system)
- [Quiz and Practice Engine](#quiz-and-practice-engine)
- [Flashcards and Spaced Repetition](#flashcards-and-spaced-repetition)
- [Mistake Tracking](#mistake-tracking)
- [AI Features](#ai-features)
- [Networking and API Integration](#networking-and-api-integration)
- [Offline-First Data Strategy](#offline-first-data-strategy)
- [Local Persistence](#local-persistence)
- [State Management](#state-management)
- [Authentication and Security](#authentication-and-security)
- [Monetization](#monetization)
- [Notifications and Engagement](#notifications-and-engagement)
- [Firebase Integration](#firebase-integration)
- [Theming and Branding](#theming-and-branding)
- [Project Structure](#project-structure)
- [Legacy Code and Migration](#legacy-code-and-migration)
- [Known Technical Debt](#known-technical-debt)
- [Testing Strategy](#testing-strategy)
- [Engineering Conventions](#engineering-conventions)
- [Production and Release Workflow](#production-and-release-workflow)
- [Debugging and Performance](#debugging-and-performance)
- [Engineering Trade-offs](#engineering-trade-offs)
- [What I Would Improve Next](#what-i-would-improve-next)
- [Getting Started](#getting-started)
- [Technology Stack](#technology-stack)
- [Portfolio Evidence](#portfolio-evidence)
- [About the Developer](#about-the-developer)
- [Project Status](#project-status)
- [License](#license)

---

# Project Overview

Bloom Learning Platform is a reusable mobile application engine for educational products.

The platform provides common infrastructure required by modern learning applications:

- Structured educational content
- Course and lesson navigation
- Quiz and practice systems
- Exam simulation
- AI-assisted learning
- AI-generated quizzes
- Smart search
- Flashcards
- Spaced repetition
- Mistake tracking
- Study planning
- Progress tracking
- Streaks
- XP and daily goals
- Leaderboards
- Friends and challenges
- Bookmarks
- Notebook functionality
- Video learning
- Offline data access
- Subscription handling
- In-app purchases
- Advertising
- Push notifications
- Local notifications
- Firebase services
- Analytics and crash monitoring
- Light and dark themes

The important engineering decision is that these capabilities are implemented as reusable platform functionality rather than being independently recreated for every subject.

The subject-specific applications can therefore focus primarily on:

1. Content
2. Branding
3. Configuration
4. Product positioning
5. Store metadata
6. Subject-specific assets

while the underlying application engine remains shared.

---

# The Engineering Problem

Building one educational application is relatively straightforward.

Maintaining a portfolio of many applications is a different engineering problem.

If every application has its own implementation of authentication, API calls, quizzes, bookmarks, caching, subscriptions, notifications, AI features, and study systems, the cost of maintenance increases with every new application.

A bug fixed in one application may still exist in several others.

A feature added to one application may need to be manually recreated elsewhere.

A change to the API layer can require changes across multiple projects.

This creates several common problems:

- Duplicated business logic
- Duplicated UI logic
- Inconsistent behavior between applications
- Repeated debugging
- Slower feature development
- Higher release-maintenance cost
- Greater risk of regressions
- Difficulty keeping applications technically consistent

Bloom was developed to solve that problem through a shared application engine.

---

# The Solution

The platform uses a reusable core with a feature-first architecture.

At a high level:

```text
Shared Engineering
        +
Subject-Specific Configuration
        +
Subject-Specific Content
        =
Independent Educational Applications
```

The goal is not to make every application identical.

The goal is to make the underlying engineering reusable while allowing each application to have its own:

- Subject
- Content
- Branding
- Assets
- Store listing
- Product configuration
- Monetization configuration

This approach makes it possible to evolve the platform without maintaining a completely separate technical foundation for every educational application.

---

# Portfolio Scale

Bloom Code Studio has independently developed and published 50+ production Android applications, primarily focused on education and learning.

The portfolio includes applications covering areas such as:

### Nursing and Clinical Education

- Clinical Nursing Skills
- Pharmacology for Nurses
- Medical-Surgical Nursing
- Maternal and Newborn Nursing
- Nursing Fundamentals
- Psychology Nursing
- Other nursing and NCLEX-focused applications

### Business and Economics

- Business Management
- Business Law and Ethics
- Business Statistics
- Economics
- Startup and Business Planning
- Workplace Skills

### Science and STEM

- Biology
- Anatomy and Physiology
- Chemistry
- Computer Science
- Data Science
- Astronomy
- Mathematics
- Algebra and Trigonometry
- 3D Printing and CAD

### Humanities and Social Sciences

- Philosophy
- Anthropology
- Lifespan Development
- Psychology
- Other social-science learning products

A flagship educational application has surpassed 1M+ Google Play downloads and has maintained a 4.3-star rating with thousands of ratings.

Store metrics naturally change over time, so current Play Store numbers should be checked directly when evaluating the live applications.

---

# My Role and Ownership

I designed and developed the platform independently as part of my work at Bloom Code Studio.

My responsibilities have covered the complete mobile product lifecycle rather than only writing individual Flutter screens.

This includes:

- Product implementation
- Flutter application architecture
- UI development
- State management
- API integration
- REST/JSON data handling
- WordPress REST API integration
- Firebase integration
- Local persistence
- Offline-first behavior
- AI feature integration
- Authentication flows
- Monetization
- Advertising
- Push notifications
- Local notifications
- Analytics
- Crash monitoring
- Debugging
- Performance improvements
- Application configuration
- Google Play releases
- Store listing management
- ASO experimentation
- Production maintenance

This project is representative of production-oriented Flutter development rather than a tutorial application or isolated coding exercise.

---

# Engineering Case Study

## From Individual Apps to a Reusable Application Platform

The platform evolved from the practical need to develop multiple educational applications efficiently.

The initial problem was straightforward: each new subject required an application with many of the same capabilities.

A typical educational product needed:

- Content browsing
- Courses and lessons
- Quizzes
- Progress tracking
- Bookmarks
- Flashcards
- Notifications
- Local storage
- API integration
- Firebase services
- Monetization
- AI-assisted features

Rebuilding these systems independently for every application would create unnecessary duplication.

The architecture therefore evolved toward a shared application engine where reusable functionality is separated from subject-specific content and configuration.

### Problem

Without a reusable foundation, multiple applications would create:

- Repeated UI implementation
- Repeated API integration
- Repeated state-management logic
- Repeated local-storage implementation
- Repeated bug fixes
- Inconsistent feature behavior
- Higher maintenance cost
- Slower product iteration

### Architectural Response

The solution was to establish reusable boundaries around:

```text
Shared Core
    +
Reusable Feature Modules
    +
Application Configuration
    +
Subject-Specific Content
```

This allows the same engineering foundation to support multiple educational products without requiring the core learning systems to be rewritten for every subject.

### Implementation

The reusable platform contains shared functionality for:

- Educational content
- Quiz and exam systems
- AI learning features
- Flashcards
- Mistake tracking
- Study planning
- Progress
- Gamification
- Notifications
- Monetization
- Local storage
- Networking
- Firebase integration

Application-specific configuration determines the subject, content source, branding, assets, and product-specific values.

### Result

The architecture has been used across a portfolio of 50+ published Android applications.

The portfolio includes applications across nursing, science, mathematics, business, finance, computer science, psychology, philosophy, and other educational categories.

A flagship educational application has surpassed 1M+ Google Play downloads.

The important result is therefore not only the number of applications published, but the ability to maintain a reusable technical foundation across multiple products.

---

# Key Engineering Challenges

## Supporting Multiple Products

The largest architectural challenge is avoiding unnecessary duplication while allowing individual applications to remain independently configurable.

The platform addresses this through shared feature modules and centralized application configuration.

---

## Managing Remote and Local Data

Educational applications depend on remote content but also need to behave reasonably when connectivity is unavailable.

The data layer therefore combines:

```text
Remote REST APIs
        +
Local Hive Storage
        +
Cache-First Access
```

This introduces additional concerns around stale data, cache updates, loading states, errors, and synchronization.

Those concerns are handled at the data/repository level instead of being duplicated throughout UI code.

---

## Integrating AI Features

AI introduces concerns that do not exist in traditional static educational applications.

The platform needs to consider:

- API security
- Usage limits
- Request validation
- Error handling
- Provider dependencies
- User experience
- Cost control

AI requests are therefore designed around an application gateway rather than exposing raw provider credentials inside the Flutter application.

---

## Production Debugging

A production application can fail in ways that are not immediately visible from the UI.

Examples include:

- API failures
- Authentication errors
- Incorrect cached state
- Firebase configuration problems
- Notification issues
- Release-build differences
- State-management problems
- Monetization behavior

The layered architecture provides defined points at which these problems can be investigated.

---

## Maintaining a Shared Codebase

A shared engine reduces duplicated development but creates another responsibility: changes to shared functionality can affect multiple applications.

This makes controlled changes, testing, configuration management, and production monitoring important parts of the development process.

---

# Technical Decisions

The following decisions describe why major technologies and architectural patterns are used in the current platform.

| Decision | Reason |
|---|---|
| Flutter | Cross-platform mobile application development with a shared Dart codebase |
| Feature-first organization | Keeps related functionality together as the application grows |
| Clean Architecture | Separates presentation, business rules, and infrastructure |
| Provider / ChangeNotifier | Lightweight state management for the current architecture |
| MVVM-style ViewModels | Keeps presentation state and interaction logic outside widgets |
| Dio | Centralized HTTP and REST communication |
| WordPress REST API | Practical content-management and content-delivery backend |
| Hive CE | Local persistence and offline-first data handling |
| Firebase | Messaging, analytics, crash monitoring, and supporting application services |
| RevenueCat | Subscription and entitlement management where configured |
| AdMob | Advertising monetization where configured |
| Gateway-mediated AI | Keeps provider credentials outside the mobile client and provides a controlled API boundary |

These decisions are specific to the requirements and evolution of this project. They are not presented as universally superior choices for every Flutter application.

---

# Production Lessons Learned

Developing and maintaining production applications has influenced the architecture in several ways.

## Production architecture must account for failure

A mobile application cannot assume that the network, backend, authentication service, or third-party provider will always behave correctly.

Loading, error, empty, cached, and retry states therefore need to be considered during feature development.

## Reusability requires discipline

A shared architecture reduces duplication, but shared code also increases the impact of changes.

Reusable modules need clear boundaries and careful regression testing.

## Offline support adds complexity

Caching improves availability and responsiveness, but introduces questions around:

- Cache freshness
- Invalidation
- Synchronization
- Storage size
- Conflicting data
- Error recovery

Offline-first design is therefore a deliberate architectural decision rather than simply adding local storage.

## AI requires backend control

AI features are different from ordinary API integrations because they can involve provider costs, sensitive credentials, rate limits, and unpredictable responses.

A controlled gateway provides a place for validation, authentication, usage restrictions, and provider abstraction.

## Technical debt is part of product evolution

The current codebase contains legacy areas from earlier development stages.

The goal is not to pretend that the project has always been perfectly structured. The goal is to identify technical debt, document it, and migrate it systematically without unnecessarily disrupting production applications.

---

# Screenshots and Product Evidence

The repository can include screenshots showing the actual product experience.

Recommended evidence includes:

| Screen | What it demonstrates |
|---|---|
| Home / Dashboard | Application navigation and learning overview |
| Quiz | Interactive assessment flow |
| AI Tutor | AI-assisted learning experience |
| Flashcards | Study and review functionality |
| Progress | Learning progress and statistics |
| Leaderboard | Gamification and engagement |
| Dark Mode | Shared theming system |

Where appropriate, live Google Play listings can also be linked from the repository so recruiters and developers can verify the published applications directly.

---

# Architecture

Bloom follows a feature-first Clean Architecture approach.

At a high level:

```text
Presentation
     |
     v
ViewModel / Provider
     |
     v
Domain
     |
     v
Repository Contract
     |
     v
Data
     |
     +------------------+
     |                  |
     v                  v
Remote Data         Local Data
Dio / REST          Hive CE
     |
     v
Backend / APIs
```

Cross-cutting services are centralized under the shared core:

```text
                 +----------------------+
                 |      Shared Core     |
                 +----------------------+
                    |    |    |    |
                    v    v    v    v
                 Network Storage Security
                    |          |
                    v          v
              Configuration  Gateway
                    |
                    v
              Monetization
```

---

# Why Feature-First Clean Architecture

The main reason for choosing this architecture is scale.

A traditional project structure organized primarily by technical type can quickly become difficult to navigate:

```text
screens/
models/
services/
providers/
repositories/
widgets/
utils/
```

As the application grows, files belonging to one feature become distributed across many directories.

Bloom instead groups feature-specific implementation together:

```text
features/
    quiz/
        data/
        domain/
        presentation/

    flashcards/
        data/
        domain/
        presentation/

    ai_tutor/
        data/
        domain/
        presentation/
```

This provides several advantages:

- Feature ownership is easier to understand
- Business logic remains separated from UI
- Data implementation can change without rewriting presentation
- Features are easier to test independently
- New functionality has a predictable location
- The codebase becomes easier to navigate as functionality grows

The shared `core/` directory contains functionality that is genuinely cross-cutting rather than feature-specific.

---

# White-Label Configuration

One of the most important parts of the platform is separating application configuration from feature implementation.

A subject-specific application should not require rewriting shared feature code simply because the subject changes.

Configuration therefore acts as the boundary between the reusable engine and an individual product.

A simplified representation is:

```dart
final class AppConfig {
  const AppConfig({
    required this.appId,
    required this.appName,
    required this.assetFolder,
    required this.contentHost,
    required this.rootCategoryId,
    required this.revenueCatApiKey,
    required this.admobAppId,
    required this.privacyPolicyUrl,
    required this.termsOfServiceUrl,
  });

  final String appId;
  final String appName;
  final String assetFolder;
  final String contentHost;
  final int rootCategoryId;

  final String revenueCatApiKey;
  final String admobAppId;

  final String privacyPolicyUrl;
  final String termsOfServiceUrl;
}
```

The actual implementation contains additional application-specific configuration.

The important design principle is:

```text
Feature Code
    |
    v
Configuration Contract
    |
    v
Current Application
```

rather than:

```text
Feature Code
    |
    +--> Biology
    +--> Nursing
    +--> Finance
    +--> Psychology
    +--> Computer Science
```

This prevents subject-specific branching from spreading throughout the codebase.

---

# Configuration and Build-Time Values

Sensitive or environment-specific values are supplied through build configuration rather than being embedded directly in feature implementation.

For example:

```bash
flutter build appbundle \
  --dart-define=REVENUECAT_KEY=... \
  --dart-define=ADMOB_APP_ID=...
```

The exact production configuration is intentionally excluded from this public case study.

The repository should never contain private provider credentials, production secrets, or private backend configuration.

---

# Application Flow

A typical content request follows this general path:

```text
User opens a lesson
        |
        v
Presentation Widget
        |
        v
Provider / ViewModel
        |
        v
Domain Use Case
        |
        v
Repository Contract
        |
        v
Repository Implementation
        |
        +--------------------+
        |                    |
        v                    v
    Hive Cache          Remote API
                             |
                             v
                       WordPress REST
                             |
                             v
                        JSON Response
                             |
                             v
                       Cache Update
                             |
                             v
                      Domain Result
                             |
                             v
                     ViewModel State
                             |
                             v
                            UI
```

The same general pattern is used across content, quizzes, study tools, and other data-driven features.

---

# Feature Modules

The platform is organized around product capabilities.

| Module | Purpose |
|---|---|
| Educational Content | Courses, lessons, structured learning material |
| Quiz Engine | Practice questions and answer evaluation |
| Exam Simulator | Exam-style practice and timed sessions |
| AI Tutor | Interactive subject-focused learning assistance |
| AI Quiz Generator | AI-assisted question generation |
| Smart Search | Search across available learning content |
| Flashcards | Review and spaced repetition |
| Mistakes | Track incorrect answers and weak areas |
| Study Plan | Structured study recommendations and progress |
| Notebook | Personal learning notes |
| Mastery | Progress and learning performance |
| Streaks | Daily learning consistency |
| Gamification | XP, goals, rewards and engagement |
| Leaderboards | Competitive progress tracking |
| Friends | Social learning features |
| Daily Goals | Daily learning targets |
| Notifications | Local and server-driven notifications |
| Monetization | Subscriptions, purchases and entitlements |
| Analytics | Product and technical analytics |
| Video Learning | Video-based learning experiences |
| Visual Learning | Visual educational content |
| Onboarding | New-user application flow |

The exact combination of modules can vary between applications depending on product configuration.

---

# Learning System

The platform is designed around a repeated learning cycle:

```text
LEARN
  ↓
PRACTICE
  ↓
MAKE MISTAKES
  ↓
ANALYZE
  ↓
IDENTIFY WEAK AREAS
  ↓
REVIEW
  ↓
PRACTICE AGAIN
  ↓
IMPROVE
```

This is implemented through several connected systems rather than treating quizzes as an isolated feature.

For example, an incorrect quiz answer can contribute to a user's mistake history, which can then influence review and future study behavior.

This connects assessment with revision instead of treating the quiz system as a standalone component.

---

# Quiz and Practice Engine

The quiz system supports structured practice and exam-style learning.

Core responsibilities include:

- Question presentation
- Answer selection
- Correctness evaluation
- Score calculation
- Progress tracking
- Quiz completion
- Mistake recording
- Review behavior
- Exam simulation

The engine is designed so that question content can change without rewriting quiz presentation and business logic.

This is particularly important for a portfolio where the same engine can serve:

```text
Biology
Nursing
Pharmacology
Accounting
Computer Science
Psychology
Mathematics
and other subjects
```

---

# Flashcards and Spaced Repetition

The platform includes flashcard-based study functionality with spaced-repetition behavior.

The implementation uses SM-2-style scheduling concepts to determine when a learning item should be reviewed.

The general lifecycle is:

```text
New Card
   ↓
First Review
   ↓
Recall Result
   ↓
Interval Calculation
   ↓
Next Review
   ↓
Repeated Reviews
   ↓
Longer Intervals
```

Flashcard state is persisted locally so that review progress remains available between sessions.

---

# Mistake Tracking

Incorrect answers are treated as useful learning data rather than simply reducing a quiz score.

The mistake system maintains records that can be used for:

- Reviewing incorrect questions
- Identifying weak topics
- Revisiting difficult material
- Supporting study planning
- Measuring improvement

This connects assessment with revision instead of treating the quiz system as a standalone component.

---

# AI Features

AI functionality is integrated into the learning experience rather than being implemented as an isolated chatbot screen.

Depending on the application configuration, AI functionality can include:

- AI Tutor
- AI Study Assistant
- AI Quiz Generator
- Smart Search
- Subject-aware learning assistance

The AI layer is designed around controlled application flows rather than exposing raw provider functionality directly to the client.

A simplified flow is:

```text
Flutter Application
        |
        v
Authenticated Request
        |
        v
Backend / Gateway
        |
        v
AI Provider
        |
        v
Validated Response
        |
        v
Flutter Application
```

The client application does not need to contain raw AI provider secrets.

This architecture also provides a place to apply:

- Authentication
- Authorization
- Rate limiting
- Request validation
- Usage limits
- Provider abstraction
- Monitoring

---

# Networking and API Integration

The networking layer uses Dio for HTTP communication.

The application integrates with REST-based backend services, including WordPress REST APIs and supporting infrastructure.

The networking layer centralizes common behavior such as:

- HTTP configuration
- Request handling
- Response processing
- Authentication
- Error handling
- Caching behavior
- Connectivity-aware behavior

The goal is to prevent individual screens and widgets from becoming responsible for API implementation details.

A typical feature therefore depends on a repository rather than directly calling Dio from a widget.

---

# Offline-First Data Strategy

Educational applications need to remain useful when connectivity is unreliable.

Bloom uses local persistence through Hive CE for structured application data and cache storage.

The general strategy is:

```text
Request Data
     |
     v
Check Local Cache
     |
   +---+---+
   |       |
 Found   Missing
   |       |
   v       v
Return   Request API
         |
         v
      Save Cache
         |
         v
      Return Data
```

This approach provides several benefits:

- Faster repeat access
- Reduced network requests
- Better behavior on unreliable connections
- Persistence between sessions
- Improved perceived application performance

Offline functionality is treated as part of the data architecture rather than as an afterthought.

---

# Local Persistence

The platform stores several categories of user and application state locally.

Examples include:

- Bookmarks
- Flashcard records
- Mistake records
- Streak state
- Completed lessons
- Notification preferences
- Notebook entries
- Cached content
- Other structured learning state

Hive adapters and generated files are produced through code generation.

Generated files should not be manually edited.

---

# State Management

Provider and `ChangeNotifier` are used as the primary state-management approach in the current platform.

The implementation follows a ViewModel-oriented pattern.

A simplified flow is:

```text
Widget
  ↓
Consumer / Selector
  ↓
ViewModel
  ↓
Use Case
  ↓
Repository
```

The platform uses scoped consumers and selectors where appropriate to reduce unnecessary widget rebuilds.

The objective is to keep state ownership understandable and predictable across a large shared codebase.

---

# Why Provider in This Codebase

Provider was selected for the current platform because it provides a relatively lightweight dependency and state-management model while the architecture already separates presentation, domain, and data responsibilities.

The decision is specific to this codebase.

It is not a claim that Provider is universally better than Riverpod or BLoC.

As the architecture evolves, state-management patterns can be evaluated based on:

- Feature complexity
- Team size
- Testability
- Event-driven requirements
- Maintainability
- Dependency management
- Migration cost

The important architectural principle is keeping state management behind clear presentation boundaries rather than coupling business logic directly to widgets.

---

# Authentication and Security

Security-sensitive responsibilities are kept outside individual feature widgets.

The platform uses secure local storage where appropriate for sensitive application values.

AI provider credentials are not intended to be shipped directly inside the mobile client.

Production systems should keep provider secrets on controlled server infrastructure and expose only the application-level API required by the client.

Build-time configuration is used for environment-specific values where appropriate.

Public repositories should never contain:

- Private API keys
- Private access tokens
- Production credentials
- Service-account files
- Signing credentials
- Private backend configuration

---

# Monetization

The platform supports a combination of free and paid functionality.

The monetization layer can include:

- Subscriptions
- One-time purchases
- Free-tier usage limits
- Advertisements
- Premium entitlements

RevenueCat is used for subscription and entitlement management where configured.

Ad monetization is integrated through the advertising layer.

The application architecture keeps monetization concerns separate from core educational functionality so that study features do not need to know the implementation details of the billing provider.

---

# Subscription Model

A simplified product model can be represented as:

| Capability | Free Tier | Premium Tier |
|---|---|---|
| Core learning content | Available with limits depending on app | Expanded access |
| AI functionality | Usage limits | Higher or expanded access |
| Exams | Usage limits depending on configuration | Expanded access |
| Advertising | Enabled | Removed where configured |
| Study tools | Available with limits depending on configuration | Expanded access |
| Additional premium features | Limited | Available |

Exact pricing and entitlements are configured per product and are resolved through the monetization system rather than hardcoded into UI widgets.

---

# Notifications and Engagement

The platform uses both local notifications and Firebase Cloud Messaging.

Local notifications can support:

- Learning reminders
- Streak reminders
- Daily goals
- Study prompts

FCM can support server-driven communication such as:

- Announcements
- Re-engagement
- Product updates
- Other configured push campaigns

Notification behavior is integrated with user preferences and application configuration.

---

# Firebase Integration

Firebase is used where appropriate for production application services.

The platform can integrate services including:

- Firebase Cloud Messaging
- Firebase Crashlytics
- Firebase Analytics
- Firebase Authentication
- Firebase Firestore

Firebase is used as an infrastructure component rather than allowing Firebase-specific code to spread throughout presentation widgets.

---

# Theming and Branding

Because the platform supports multiple applications, visual identity needs to be configurable without duplicating the application architecture.

Shared theming provides:

- Light mode
- Dark mode
- Centralized colors
- Typography
- Reusable UI components
- Consistent spacing and visual behavior

Subject-specific applications can then provide their own visual identity while reusing the underlying UI infrastructure.

---

# Project Structure

The current project follows a feature-first structure under `lib/src`.

A simplified representation is:

```text
lib/
├── firebase_options.dart
├── hive_registrar.g.dart
│
├── model/
│   └── legacy/shared models
│
├── in-app purchase/
│   └── legacy purchase implementation
│
├── utils/
│   └── legacy utilities
│
└── src/
    │
    ├── core/
    │   ├── monetization/
    │   ├── network/
    │   ├── security/
    │   ├── services/
    │   ├── notifications/
    │   ├── storage/
    │   ├── theme/
    │   ├── utils/
    │   └── widgets/
    │
    └── features/
        ├── ai/
        ├── ai_tutor/
        ├── ai_history/
        ├── quiz/
        ├── quiz_engine/
        ├── exam_simulator/
        ├── flashcards/
        ├── mistakes/
        ├── notebook/
        ├── mastery/
        ├── streak/
        ├── gamification/
        ├── leaderboards/
        ├── daily_goals/
        ├── friends/
        ├── engagement/
        ├── retention/
        ├── educational_content/
        ├── smart_search/
        ├── smart_study_plan/
        ├── monetization/
        ├── notifications/
        ├── onboarding/
        ├── analytics/
        ├── cosmetics/
        ├── discord/
        ├── video_companion/
        └── visual_learning/
```

Individual features are progressively organized around:

```text
feature/
├── data/
├── domain/
└── presentation/
```

This is the direction for new development.

---

# Legacy Code and Migration

The repository contains legacy areas from earlier stages of development.

These include:

```text
lib/model/
lib/in-app purchase/
lib/utils/
```

They are documented rather than hidden.

The project is being progressively migrated toward:

```text
lib/src/core/
lib/src/features/
```

New functionality should follow the feature-first structure rather than extending legacy locations.

Documenting migration boundaries provides a more accurate picture of a production codebase than presenting it as if it had always been perfectly structured.

---

# Known Technical Debt

Current technical debt includes:

- Legacy top-level model locations
- Legacy utility locations
- An older in-app purchase module
- Migration toward the feature-first structure
- Historical naming conventions that should be normalized
- Generated code that must remain synchronized with Hive models

One example is the historical directory:

```text
in-app purchase/
```

The space in the directory name is not desirable for a modern Dart project structure and is a candidate for migration to:

```text
in_app_purchase/
```

This debt is known, documented, and part of an ongoing refactoring process.

---

# Testing Strategy

Testing is focused on business logic and high-risk application behavior.

The highest-value test targets include:

- Quiz scoring
- Study logic
- Flashcard scheduling
- Mistake tracking
- Entitlement behavior
- Usage limits
- Repository behavior
- Data transformations
- Critical state transitions

Widget tests are particularly useful for interaction-heavy and rebuild-sensitive areas such as:

- Quiz flows
- Streak displays
- Critical learning screens
- State-dependent UI

The long-term goal is to keep as much business logic as practical in testable Dart code rather than embedding rules directly inside widgets.

---

# Engineering Conventions

The project follows several conventions.

## Feature-first organization

New functionality belongs under:

```text
lib/src/features/<feature_name>/
```

with appropriate:

```text
data/
domain/
presentation/
```

boundaries.

## Dependency direction

Presentation should depend on domain abstractions.

Data implementations should implement domain contracts.

Avoid direct presentation-to-data coupling.

## Strong typing

Prefer explicit types over unnecessary `dynamic`.

Use structured result types where appropriate rather than allowing exceptions and loosely typed values to cross every architectural boundary.

## Const usage

Use `const` constructors, widgets, and values wherever practical.

This improves widget immutability and can reduce unnecessary rebuild work.

## Resource cleanup

Controllers, subscriptions, listeners, streams, and other disposable resources should be cleaned up appropriately.

```dart
@override
void dispose() {
  controller.dispose();
  subscription?.cancel();
  super.dispose();
}
```

## Offline awareness

New data-driven features should consider:

- Cache behavior
- Loading states
- Empty states
- Network failures
- Previously cached data
- Retry behavior

Offline behavior should be deliberate rather than accidental.

---

# Production and Release Workflow

The applications are developed with production distribution in mind.

The general release lifecycle is:

```text
Development
    ↓
Local Testing
    ↓
API / Firebase Testing
    ↓
Release Build
    ↓
Internal Validation
    ↓
Google Play Console
    ↓
Production Release
    ↓
Crash / Analytics Monitoring
    ↓
Bug Fixes and Iteration
```

Production ownership includes more than implementing features.

It also requires handling:

- Android build configuration
- Application IDs
- Release configuration
- Signing
- Store requirements
- Privacy requirements
- Monetization configuration
- Firebase configuration
- Production API behavior
- Application updates
- Play Console releases

---

# Debugging and Performance

Production mobile development regularly requires investigating issues that are not visible from the UI alone.

Areas worked on across the application portfolio include:

- API failures
- Authentication problems
- Caching issues
- State-management bugs
- Rebuild behavior
- Memory-related problems
- Incorrect local state
- Release-build issues
- Firebase integration problems
- Notification behavior
- Monetization behavior

The architecture helps isolate these problems.

For example:

```text
UI problem
   ↓
Check ViewModel state
   ↓
Check domain result
   ↓
Check repository
   ↓
Check local cache
   ↓
Check network request
   ↓
Check backend response
```

This makes debugging more systematic than placing API calls and business rules directly inside widgets.

---

# Engineering Trade-offs

Architecture is a set of trade-offs rather than a collection of universally correct rules.

Several decisions in this project reflect that principle.

## Provider vs. other state-management patterns

Provider provides a relatively low-ceremony approach for the current architecture.

The trade-off is that complex asynchronous workflows can require more discipline around ViewModels and state transitions.

## Hive vs. a server-only data model

Local persistence increases application complexity because data synchronization and invalidation need to be considered.

The benefit is improved offline behavior and faster access to previously retrieved information.

## WordPress REST as a content backend

WordPress provides a practical content-management workflow for a large educational catalog.

The trade-off is that a general-purpose CMS does not provide all the guarantees or domain modeling capabilities of a purpose-built learning backend.

The architecture therefore isolates WordPress behind data-layer contracts rather than allowing WordPress-specific assumptions to spread through the application.

## Shared engine vs. independent applications

A shared engine reduces duplicated engineering effort.

The trade-off is that a change to shared functionality can affect multiple applications.

This makes regression testing, configuration discipline, and controlled releases important.

---

# What I Would Improve Next

The platform is an evolving production codebase rather than a finished architectural exercise.

Areas that can continue to improve include:

- Completing legacy-to-feature-first migration
- Increasing automated test coverage
- Further isolating infrastructure dependencies
- Improving error/result modeling
- Strengthening dependency injection
- Improving CI/CD automation
- Improving observability
- Refining offline synchronization
- Improving modularity between shared and product-specific code
- Evaluating state-management patterns as feature complexity grows

These improvements should be evaluated against actual product requirements rather than introduced simply for architectural fashion.

---

# Getting Started

## Requirements

The project is based on a modern Flutter/Dart environment.

Recommended requirements for the current codebase include:

- Flutter stable
- Dart version compatible with the project SDK constraints
- Android Studio or equivalent Android tooling
- Xcode for iOS development where applicable
- Firebase configuration
- Access to the required backend environment
- Required build-time configuration values

Always use the SDK constraints defined by the project's `pubspec.yaml` as the authoritative version requirement.

## Installation

Clone the repository:

```bash
git clone https://github.com/muhammadsaadbloom/<repository-name>.git
cd <repository-name>
```

Install dependencies:

```bash
flutter pub get
```

Configure Firebase if required:

```bash
dart pub global activate flutterfire_cli
flutterfire configure
```

Generate required code:

```bash
dart run build_runner build --delete-conflicting-outputs
```

Run the application:

```bash
flutter run
```

Production configuration is intentionally excluded from this public case study.

---

# Code Generation

Hive adapters and other generated files should not be manually edited.

Generate code with:

```bash
dart run build_runner build --delete-conflicting-outputs
```

During active development:

```bash
dart run build_runner watch --delete-conflicting-outputs
```

Whenever a Hive model changes, generated adapters should be regenerated before testing the application.

---

# Repository Design Principles

The platform follows a few core principles:

```text
Reusable over duplicated

Explicit dependencies over hidden dependencies

Domain rules over widget-level business logic

Configuration over hardcoded subject behavior

Cache-aware over network-dependent

Production behavior over demo behavior

Documented technical debt over hidden technical debt
```

These principles guide the ongoing evolution of the project.

---

# Technology Stack

| Category | Technology |
|---|---|
| Mobile Framework | Flutter |
| Language | Dart |
| State Management | Provider / ChangeNotifier |
| Architecture | Clean Architecture |
| Presentation Pattern | MVVM-style ViewModels |
| Networking | Dio |
| APIs | REST / JSON |
| Content Backend | WordPress REST API |
| Local Storage | Hive CE |
| Push Notifications | Firebase Cloud Messaging |
| Local Notifications | Local notification infrastructure |
| Crash Monitoring | Firebase Crashlytics |
| Analytics | Firebase Analytics |
| Authentication | Firebase / application-specific authentication |
| AI | Gateway-mediated AI services |
| Subscriptions | RevenueCat |
| Advertising | AdMob / configured mediation |
| Version Control | Git / GitHub |
| Distribution | Google Play Console |
| Code Generation | build_runner / generated Hive adapters |

---

# Portfolio Evidence

The strongest evidence for this project is not the architecture diagram alone.

The platform has been used to build and maintain a portfolio of real applications distributed through Google Play.

The portfolio includes applications for:

- Nursing
- Pharmacology
- Biology
- Anatomy and Physiology
- Chemistry
- Computer Science
- Data Science
- Business
- Finance and Accounting
- Economics
- Mathematics
- Psychology
- Philosophy
- Workplace skills
- Other educational subjects

A flagship educational application has achieved more than 1M downloads on Google Play.

The portfolio demonstrates the practical use of the architecture across multiple products rather than only a single sample application.

---

# Why This Repository Matters as a Case Study

A typical Flutter portfolio project can demonstrate that someone knows how to build:

```text
A screen
A form
An API call
A Firebase feature
A navigation flow
```

Bloom demonstrates a different problem:

```text
How do you maintain a reusable mobile product
across many applications without duplicating
the entire engineering stack?
```

That problem introduces concerns around:

- Architecture
- Configuration
- Abstraction
- Data ownership
- Caching
- Offline behavior
- State management
- Monetization
- Security
- AI integration
- Notifications
- Testing
- Technical debt
- Production releases
- Long-term maintenance

That is the reason this repository is presented as an engineering case study rather than simply a collection of Flutter screens.

---

# About the Developer

## Muhammad Saad

Flutter Mobile Developer and Founder of Bloom Code Studio.

I have 3+ years of hands-on Flutter development experience and have independently designed, built, maintained, and published 50+ production Android applications.

My work focuses primarily on:

- Flutter
- Dart
- Mobile application architecture
- Provider and MVVM-style state management
- Clean Architecture
- REST APIs
- WordPress REST APIs
- Firebase
- Hive and offline-first storage
- AI-powered application features
- Monetization
- Google Play publishing
- Debugging and production maintenance

I have taken applications from development through release and continued maintenance, which has given me experience with the parts of mobile development that happen after the initial UI implementation.

The Bloom portfolio includes a flagship educational application with 1M+ Google Play downloads and thousands of ratings.

My current focus is continuing to improve as a professional Flutter engineer through production work, stronger engineering practices, collaboration, and increasingly maintainable application architecture.

---

# GitHub

https://github.com/muhammadsaadbloom

---

# Engineering Perspective

The platform is not intended to demonstrate that every architectural decision is final.

It demonstrates an ongoing engineering process:

```text
Build
  ↓
Release
  ↓
Observe
  ↓
Debug
  ↓
Refactor
  ↓
Reuse
  ↓
Scale Across Products
```

The architecture has evolved in response to real product requirements, rather than being designed only as a theoretical sample project.

That distinction is important to this case study: the repository represents production-oriented Flutter development, including the constraints and technical debt that naturally accompany a growing application portfolio.

---

# Project Status

Active production platform.

The architecture and feature set continue to evolve as new educational applications are developed, existing applications are maintained, and production requirements change.

---

# License

MIT License, where applicable to the source code contained in this repository.

Third-party services, trademarks, educational content, application assets, and external resources remain subject to their respective licenses and terms.
