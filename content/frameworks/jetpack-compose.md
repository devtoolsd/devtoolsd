---
name: Jetpack Compose
slug: jetpack-compose
language: kotlin
description: Android's modern declarative UI toolkit — Kotlin-first, composable functions replacing XML layouts.
website: https://developer.android.com/jetpack/compose
github: androidx/androidx
year: 2020
pricing: free
open_source: true
license: Apache-2.0
tool_type: mobile
tags: [android, mobile, kotlin, ui, declarative, google, compose]
related_frameworks: [swiftui]
features:
  - "Composable functions — build UI by calling Kotlin functions, no XML"
  - "Unidirectional data flow with `remember` and `mutableStateOf`"
  - "Rich animation APIs — `animate*AsState`, `AnimatedVisibility`, transitions"
  - "Material 3 components built in — Scaffold, TopAppBar, NavigationBar"
  - "Interoperability with View-based layouts via `AndroidView`"
  - "Compose Multiplatform — share UI code with iOS, desktop, and web"
  - "Lazy layouts — `LazyColumn`, `LazyRow`, `LazyGrid` for large lists"
  - "Preview composables in Android Studio without a device"
install:
  gradle: "implementation(\"androidx.compose.ui:ui\") // in app/build.gradle.kts"
---

Jetpack Compose replaces Android's XML layout system with composable Kotlin functions that describe UI as a function of state. Its unidirectional data flow, state hoisting, and rich animation APIs make complex UIs simpler to build and test. Compose Multiplatform extends it to iOS, desktop, and web — making Compose the most promising path toward a unified Kotlin UI layer across platforms.

## Quick start

```kotlin
// build.gradle.kts — ensure Compose is enabled
android {
    buildFeatures { compose = true }
    composeOptions {
        kotlinCompilerExtensionVersion = "1.5.x"
    }
}
dependencies {
    implementation("androidx.compose.material3:material3")
    implementation("androidx.activity:activity-compose")
}
```

```kotlin
// MainActivity.kt
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            MaterialTheme {
                CounterScreen()
            }
        }
    }
}

@Composable
fun CounterScreen() {
    var count by remember { mutableIntStateOf(0) }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text(text = "Count: $count", style = MaterialTheme.typography.headlineLarge)
        Spacer(modifier = Modifier.height(16.dp))
        Button(onClick = { count++ }) {
            Text("Increment")
        }
    }
}

@Preview(showBackground = true)
@Composable
fun CounterPreview() {
    MaterialTheme { CounterScreen() }
}
```

## When to use

Jetpack Compose is the recommended way to build new Android UI. Google's own apps (Gmail, Maps) are migrating to Compose. For greenfield Android apps, Compose is the clear choice. For existing View-based apps, Compose integrates incrementally — you can mix Compose and Views in the same activity. For cross-platform mobile, Compose Multiplatform is maturing, but Flutter and React Native are more production-proven for iOS today.
