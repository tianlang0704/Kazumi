---
name: Kazumi
description: "Core workspace instructions for Kazumi - A Flutter-based media application"
---

# Kazumi Workspace Instructions

You are an expert Flutter developer working on **Kazumi**, a cross-platform media application built with Flutter, MobX, and Flutter Modular.

## Project Stack & Architecture

- **Framework**: Flutter (Supports Windows, Linux, Android, iOS, Web)
- **State Management**: [MobX](https://pub.dev/packages/mobx) (uses `mobx` and `flutter_mobx`)
- **Dependency Injection & Routing**: [Flutter Modular](https://pub.dev/packages/flutter_modular)
- **Database**: [Hive (hive_ce)](https://pub.dev/packages/hive_ce) for local persistence
- **Networking**: [Dio](https://pub.dev/packages/dio) for HTTP requests
- **Multimedia**: [media_kit](https://pub.dev/packages/media_kit) for video/audio playback

## Command Reference

### Build & Run
- **Install dependencies**: `flutter pub get`
- **Run app**: `flutter run`
- **Build (Windows)**: `flutter build windows`

### Code Generation
Always run build_runner after modifying MobX stores or Hive models:
- **Build once**: `dart run build_runner build --delete-conflicting-outputs`
- **Watch mode**: `dart run build_runner watch --delete-conflicting-outputs`

### Testing
- **Run all tests**: `flutter test`

## Development Conventions

### 1. State Management (MobX)
- Store logic in `*Controller` classes extending `Store`.
- Use `@observable` for reactive state and `@action` for modifications.
- Wrap UI components that read observables in an `Observer` widget.
- Example pattern: [lib/pages/info/info_controller.dart](lib/pages/info/info_controller.dart)

### 2. Dependency Injection & Routing (Modular)
- Define `binds` and `routes` in `*Module` classes.
- Use `Modular.get<T>()` for dependency retrieval.
- Navigate using `Modular.to.pushNamed()`.
- Root module: [lib/app_module.dart](lib/app_module.dart)

### 3. File Structure
- `lib/modules/`: Business logic, models, and service-level components.
- `lib/pages/`: UI screens and their corresponding MobX controllers.
- `lib/repositories/`: Data abstraction layers (History, Collections, etc.).
- `lib/request/`: API clients and Dio interceptors.

### 4. Local Persistence (Hive)
- Annotate data models with `@HiveType` and fields with `@HiveField`.
- Register adapters in [lib/main.dart](lib/main.dart) or via generated `hive_registrar.g.dart`.

## External Resources
- [Main README](README.md) - Project overview and roadmap.
- [BBCode Documentation](lib/bbcode/README.md) - Details on the custom BBCode engine.
- [Official Website](https://kazumi.app/docs) - User and developer documentation.
