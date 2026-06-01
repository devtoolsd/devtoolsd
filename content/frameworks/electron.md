---
name: Electron
slug: electron
language: javascript
description: Build cross-platform desktop apps with JavaScript, HTML, and CSS — powers VS Code, Slack, Figma, and thousands of other apps.
logo: https://upload.wikimedia.org/wikipedia/commons/9/91/Electron_Software_Framework_Logo.svg
website: https://electronjs.org
github: electron/electron
year: 2013
pricing: free
open_source: true
license: MIT
tool_type: desktop
tags: [desktop, cross-platform, nodejs, chromium, javascript, gui]
related_frameworks: [tauri]
features:
  - "Ship Web UIs as desktop apps for Windows, macOS, and Linux"
  - "Full Node.js access — file system, native modules, OS APIs"
  - "Chromium rendering — your web code runs exactly as in a browser"
  - "Auto-updater built in via electron-updater"
  - "Native OS integration — menus, tray icons, notifications, dialogs"
  - "IPC (Inter-Process Communication) between main and renderer processes"
  - "Code signing and packaging via Electron Forge or Electron Builder"
  - "Context isolation and sandboxing for security"
install:
  npm: "npm init electron-app@latest my-app"
  npx: "npx create-electron-app@latest my-app"
---

Electron bundles Chromium and Node.js into a single package, letting web developers ship desktop apps for Windows, macOS, and Linux without learning native SDKs. VS Code, Slack, Figma, Discord, and 1Password all use Electron. Its main trade-offs — large bundle size (~100MB+) and higher memory usage than native apps — led to Tauri as a lighter alternative using the OS webview instead of bundled Chromium.

## Quick start

```bash
npm init electron-app@latest my-app -- --template=webpack
cd my-app
npm start
```

```javascript
// src/main.js — Main process (Node.js)
const { app, BrowserWindow, ipcMain } = require('electron')
const path = require('path')

function createWindow() {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js'),
      contextIsolation: true,
    },
  })
  win.loadFile('src/index.html')
}

app.whenReady().then(createWindow)
app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit()
})
```

```javascript
// src/preload.js — Bridge between main and renderer
const { contextBridge, ipcRenderer } = require('electron')

contextBridge.exposeInMainWorld('electronAPI', {
  readFile: (path) => ipcRenderer.invoke('read-file', path),
})
```

```html
<!-- src/index.html — Renderer process (browser) -->
<button id="readBtn">Read File</button>
<script>
  document.getElementById('readBtn').addEventListener('click', async () => {
    const contents = await window.electronAPI.readFile('/etc/hosts')
    console.log(contents)
  })
</script>
```

## When to use

Electron is the right choice when you want to ship a desktop app quickly using your existing web development skills and have access to full Node.js APIs. The large install size (~150MB) is acceptable for developer tools and enterprise apps. For a lighter desktop app with better performance and smaller bundle, Tauri (Rust backend, OS webview) is the modern alternative. For apps that don't need native OS access, a PWA might be sufficient.
