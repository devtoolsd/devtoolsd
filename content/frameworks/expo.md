---
name: Expo
slug: expo
language: typescript
description: React Native framework and platform — managed workflow, EAS Build, and over-the-air updates for cross-platform mobile apps.
logo: https://expo.dev/static/images/blog/expo-logo.png
website: https://expo.dev
github: expo/expo
year: 2015
pricing: freemium
open_source: true
license: MIT
tool_type: mobile
tags: [mobile, ios, android, react-native, ota, cross-platform, typescript]
related_frameworks: [react-native, flutter]
features:
  - "Managed SDK — camera, notifications, maps, sensors with no native setup"
  - "Expo Router — file-based navigation for React Native apps"
  - "EAS Build — cloud builds for iOS and Android without a Mac"
  - "Over-the-air updates via EAS Update (ship JS changes without App Store review)"
  - "Expo Go — scan a QR code to preview your app instantly on device"
  - "Universal apps — web and native from one codebase via `expo-router`"
  - "TypeScript-first with auto-generated types for native modules"
  - "Works with React Native bare workflow for full native control"
install:
  npm: "npx create-expo-app@latest my-app"
  yarn: "yarn create expo-app my-app"
---

Expo wraps React Native with a managed SDK of pre-built native modules (camera, notifications, maps), a hosted build service (EAS Build), and over-the-air JavaScript updates. The Expo Router provides file-based navigation that mirrors Next.js conventions. For most React Native projects, Expo is the recommended starting point — you can always eject to the bare workflow if you need custom native code.

## Quick start

```bash
npx create-expo-app@latest my-app --template blank-typescript
cd my-app
npx expo start
# Press 'i' for iOS simulator, 'a' for Android, 'w' for web
```

```tsx
// app/(tabs)/index.tsx — Expo Router file-based route
import { StyleSheet, Text, View, TouchableOpacity } from 'react-native'
import { Link } from 'expo-router'
import { useState } from 'react'

export default function HomeScreen() {
  const [count, setCount] = useState(0)

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Welcome to Expo</Text>
      <TouchableOpacity onPress={() => setCount(c => c + 1)} style={styles.button}>
        <Text style={styles.buttonText}>Tapped {count} times</Text>
      </TouchableOpacity>
      <Link href="/settings" style={styles.link}>Go to Settings →</Link>
    </View>
  )
}

const styles = StyleSheet.create({
  container: { flex: 1, alignItems: 'center', justifyContent: 'center', gap: 16 },
  title: { fontSize: 24, fontWeight: 'bold' },
  button: { backgroundColor: '#0ea5e9', padding: 12, borderRadius: 8 },
  buttonText: { color: '#fff', fontWeight: '600' },
  link: { color: '#0ea5e9', marginTop: 8 },
})
```

## When to use

Expo is the recommended way to start any new React Native project. Its SDK removes the complexity of native module linking, and EAS Build lets you produce App Store-ready binaries without a Mac or Android Studio. For apps that need deep custom native modules not in the Expo SDK, the bare workflow gives full access. Compared to bare React Native, Expo trades some flexibility for a significantly better developer experience.
