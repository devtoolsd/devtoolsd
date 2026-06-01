---
name: React Native
slug: react-native
language: javascript
description: Build native iOS and Android apps using React — bridge to native components, shared logic with web React codebases.
logo: https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg
website: https://reactnative.dev
github: facebook/react-native
year: 2015
pricing: free
open_source: true
license: MIT
tool_type: mobile
tags: [mobile, ios, android, cross-platform, react, javascript, meta]
related_frameworks: [flutter, expo, ionic]
features:
  - "True native UI components — renders real iOS and Android views, not a WebView"
  - "Shared JavaScript business logic between iOS and Android"
  - "Reuse React component patterns and hooks from web development"
  - "New Architecture — JSI and Fabric eliminate the JS bridge for low-latency native calls"
  - "Over-the-air updates with Expo EAS Update (no App Store submission)"
  - "Access to device APIs — camera, GPS, notifications via community libraries"
  - "Fast Refresh for instant feedback during development"
  - "Expo managed and bare workflows for flexible project setup"
install:
  npm: "npx create-expo-app my-app"
  yarn: "yarn create expo-app my-app"
---

React Native renders genuine native UI components — not a WebView — using React's component model and JavaScript business logic. The New Architecture (JSI, Fabric, TurboModules) eliminated the JavaScript bridge, delivering significantly lower latency for native module calls. Used at Meta, Microsoft, Shopify, and thousands of apps in production. Expo is the recommended way to start new React Native projects — it provides a curated SDK, EAS Build for cloud builds, and OTA updates.

## Quick start

```bash
# Start with Expo (recommended)
npx create-expo-app my-app --template blank-typescript
cd my-app
npx expo start
```

```tsx
// app/(tabs)/index.tsx
import { useState } from 'react'
import { View, Text, StyleSheet, TouchableOpacity } from 'react-native'

export default function HomeScreen() {
  const [count, setCount] = useState(0)

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Hello React Native</Text>
      <Text style={styles.count}>{count}</Text>
      <TouchableOpacity style={styles.button} onPress={() => setCount(c => c + 1)}>
        <Text style={styles.buttonText}>Increment</Text>
      </TouchableOpacity>
    </View>
  )
}

const styles = StyleSheet.create({
  container: { flex: 1, alignItems: 'center', justifyContent: 'center' },
  title: { fontSize: 24, fontWeight: 'bold', marginBottom: 16 },
  count: { fontSize: 48, marginBottom: 24 },
  button: { backgroundColor: '#fb923c', paddingHorizontal: 24, paddingVertical: 12, borderRadius: 8 },
  buttonText: { color: '#fff', fontWeight: '600' },
})
```

## When to use

React Native is ideal when you're building a mobile app and your team already knows React. Code sharing between web and mobile (components, hooks, business logic) is a major productivity win. Expo simplifies the build and distribution pipeline. Flutter is a strong alternative with better performance for graphically intensive apps. For a pure web-based mobile experience with device access, Capacitor (Ionic) is simpler to set up but doesn't render native views.
