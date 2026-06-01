---
name: SwiftUI
slug: swiftui
language: swift
description: Apple's declarative UI framework — build native apps for iOS, macOS, watchOS, and tvOS with a single Swift codebase.
website: https://developer.apple.com/xcode/swiftui/
year: 2019
pricing: free
open_source: false
license: Proprietary
tool_type: mobile
tags: [ios, macos, mobile, apple, ui, declarative, cross-platform]
related_frameworks: [uikit, jetpack-compose]
features:
  - "Declarative syntax — describe the UI as a function of state"
  - "Runs across iOS, macOS, watchOS, tvOS, and visionOS"
  - "`@State`, `@Binding`, `@ObservedObject`, `@EnvironmentObject` for reactivity"
  - "Animations and transitions with minimal code"
  - "Swift Concurrency integration — `async/await` in `task` modifiers"
  - "Previews in Xcode for instant visual feedback"
  - "Navigation APIs — `NavigationStack`, `NavigationSplitView`"
  - "SwiftData for persistence (Swift-native Core Data replacement)"
install:
  xcode: "Create a new Xcode project and select SwiftUI as the interface"
---

SwiftUI replaced UIKit's imperative model with a declarative syntax where UI is a function of state. Property wrappers like `@State`, `@Binding`, and `@ObservedObject` handle reactivity. SwiftUI runs across the entire Apple platform family, and Apple has made clear it is the future of Apple platform development. New APIs in iOS 17+ have significantly closed the gaps with UIKit.

## Quick start

```swift
// Open Xcode → New Project → iOS App → Interface: SwiftUI
```

```swift
// ContentView.swift
import SwiftUI

struct Post: Identifiable {
    let id: UUID = UUID()
    var title: String
    var body: String
}

struct ContentView: View {
    @State private var posts: [Post] = [
        Post(title: "Hello SwiftUI", body: "Getting started."),
    ]
    @State private var showingForm = false

    var body: some View {
        NavigationStack {
            List(posts) { post in
                NavigationLink(destination: PostDetailView(post: post)) {
                    VStack(alignment: .leading) {
                        Text(post.title).font(.headline)
                        Text(post.body).font(.subheadline).foregroundColor(.secondary)
                    }
                }
            }
            .navigationTitle("Posts")
            .toolbar {
                Button("Add") { showingForm = true }
            }
            .sheet(isPresented: $showingForm) {
                NewPostForm(posts: $posts)
            }
        }
    }
}

struct PostDetailView: View {
    let post: Post

    var body: some View {
        VStack(alignment: .leading, spacing: 16) {
            Text(post.title).font(.largeTitle).bold()
            Text(post.body).font(.body)
            Spacer()
        }
        .padding()
        .navigationTitle(post.title)
        .navigationBarTitleDisplayMode(.inline)
    }
}
```

## When to use

SwiftUI is the right choice for any new Apple platform app — Apple is investing heavily in SwiftUI-only APIs. For iOS 16+ targets, SwiftUI is mature enough for production. For apps that need fine-grained control over performance, custom animations, or complex collections, UIKit interoperability via `UIViewRepresentable` fills the gaps. For cross-platform mobile (iOS + Android), Flutter or React Native avoid platform-specific code. SwiftUI and Jetpack Compose are converging on similar declarative models, making skills transferable between Apple and Android development.
