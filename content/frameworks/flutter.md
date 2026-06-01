---
name: Flutter
slug: flutter
language: dart
description: Google's UI toolkit for building natively compiled apps for mobile, web, and desktop from a single Dart codebase.
logo: https://upload.wikimedia.org/wikipedia/commons/1/17/Google-flutter-logo.png
website: https://flutter.dev
github: flutter/flutter
year: 2017
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: mobile
tags: [mobile, ios, android, cross-platform, dart, desktop, web, google]
related_frameworks: [react-native, ionic]
features:
  - "Single codebase for iOS, Android, web, macOS, Windows, and Linux"
  - "Impeller graphics engine — renders every pixel directly, no native widgets"
  - "Hot reload and hot restart for instant UI feedback during development"
  - "Rich widget library — Material Design and Cupertino (iOS-style) built in"
  - "Dart's strong typing and null safety for reliable codebases"
  - "Platform channels for calling native Swift/Kotlin code"
  - "Riverpod, Bloc, and Provider for state management"
  - "Pixel-perfect consistency across platforms"
install:
  flutter: "flutter create my_app && cd my_app && flutter run"
---

Flutter renders UI with its own Impeller graphics engine rather than native widgets — every pixel is Flutter's, enabling pixel-perfect consistency across platforms. Hot reload, a rich widget library, and strong Dart tooling make it one of the fastest cross-platform UI development experiences. Flutter is used at Google, BMW, eBay, and thousands of apps on the App Store and Play Store.

## Quick start

```bash
# Install Flutter SDK from https://flutter.dev/docs/get-started/install
flutter create my_app
cd my_app
flutter run
```

```dart
// lib/main.dart
import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      home: const CounterPage(),
    );
  }
}

class CounterPage extends StatefulWidget {
  const CounterPage({super.key});

  @override
  State<CounterPage> createState() => _CounterPageState();
}

class _CounterPageState extends State<CounterPage> {
  int _count = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Counter')),
      body: Center(
        child: Text('$_count', style: Theme.of(context).textTheme.displayLarge),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () => setState(() => _count++),
        child: const Icon(Icons.add),
      ),
    );
  }
}
```

## When to use

Flutter is the best choice when you need pixel-perfect UI consistency across iOS, Android, and potentially desktop, and your team is willing to learn Dart. Its performance and visual fidelity are unmatched in the cross-platform space. React Native is a better choice if your team is deep in JavaScript and wants to share code with a web React codebase. For apps primarily using native platform UIs (maps, media players), React Native's native widget rendering may look more "at home" on each platform.
