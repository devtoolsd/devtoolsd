---
name: Ionic
slug: ionic
language: typescript
description: Cross-platform mobile framework using web technologies — Angular, React, or Vue components rendered in a native WebView.
logo: https://upload.wikimedia.org/wikipedia/commons/b/b6/Ioniclogo.svg
website: https://ionicframework.com
github: ionic-team/ionic-framework
year: 2013
pricing: freemium
open_source: true
license: MIT
tool_type: mobile
tags: [mobile, ios, android, pwa, web-technologies, angular, react, vue]
related_frameworks: [react-native, flutter, capacitor]
features:
  - "Works with Angular, React, and Vue — no new framework to learn"
  - "Native-like UI components that adapt to iOS and Android design patterns"
  - "Capacitor for native device APIs — camera, GPS, notifications, biometrics"
  - "Progressive Web App support — deploy the same app as PWA and native"
  - "Ionic Studio and AppFlow for CI/CD and live reload"
  - "Rich component library: lists, cards, modals, slides, forms"
  - "Dark mode and theming via CSS custom properties"
  - "Offline-first capabilities via Capacitor Preferences and SQLite"
install:
  npm: "npm install -g @ionic/cli && ionic start my-app tabs --type react"
  npx: "npx @ionic/cli start my-app tabs --type=react"
---

Ionic wraps web app UIs in a native shell using Capacitor (or Cordova), giving access to native device APIs while writing HTML, CSS, and TypeScript. It ships native mobile apps and progressive web apps from the same codebase. Its component library mimics native iOS and Android UI patterns for each platform, switching styles based on the runtime platform.

## Quick start

```bash
npm install -g @ionic/cli
ionic start my-app tabs --type react
cd my-app
ionic serve
```

```tsx
// src/pages/Home.tsx
import {
  IonContent, IonHeader, IonPage, IonTitle, IonToolbar,
  IonList, IonItem, IonLabel, IonButton, useIonToast
} from '@ionic/react'
import { useState } from 'react'

const Home: React.FC = () => {
  const [items] = useState(['Item 1', 'Item 2', 'Item 3'])
  const [present] = useIonToast()

  return (
    <IonPage>
      <IonHeader>
        <IonToolbar>
          <IonTitle>Home</IonTitle>
        </IonToolbar>
      </IonHeader>
      <IonContent fullscreen>
        <IonList>
          {items.map(item => (
            <IonItem key={item}>
              <IonLabel>{item}</IonLabel>
            </IonItem>
          ))}
        </IonList>
        <IonButton expand="block" onClick={() =>
          present({ message: 'Hello from Ionic!', duration: 2000 })
        }>
          Show Toast
        </IonButton>
      </IonContent>
    </IonPage>
  )
}

export default Home
```

## When to use

Ionic is ideal for teams with strong web development experience who need a mobile app quickly. It's particularly efficient for PWAs that also need a native shell — one codebase serves both. Compared to React Native and Flutter, Ionic uses a WebView which can have performance limitations for animations and complex interactions. For performance-sensitive apps (games, media, camera-heavy), React Native or Flutter are better choices.
