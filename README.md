# Crypto-KMM

Crypto-KMM is a Kotlin Multiplatform / Compose Multiplatform starter project. The repository currently contains a generated-style `CurrencyApp` project that targets Android and iOS with a shared Compose UI.

The current app is a baseline KMM experiment: it renders a shared Compose screen with a button, animated content, the Compose Multiplatform logo, and a platform-specific greeting.

## Current Features

- Kotlin Multiplatform project targeting Android and iOS.
- Shared Compose Multiplatform UI in `commonMain`.
- Android entry point using `ComponentActivity` and `setContent`.
- iOS entry point using SwiftUI with a `UIViewControllerRepresentable` wrapper.
- Shared `expect/actual` platform API for Android and iOS.
- Compose resources through `composeResources`.
- Kotlin 2.0 and Compose Multiplatform setup.

## Tech Stack

- Kotlin Multiplatform
- Compose Multiplatform
- Android Gradle Plugin
- SwiftUI iOS host app
- Gradle Version Catalog

## Project Structure

```text
.
├── README.md
└── CurrencyApp
    ├── composeApp
    │   ├── src/commonMain/kotlin
    │   │   ├── App.kt          # Shared Compose UI
    │   │   ├── Greeting.kt     # Shared greeting helper
    │   │   └── Platform.kt     # expect platform contract
    │   ├── src/androidMain
    │   │   ├── kotlin          # Android actual platform implementation and MainActivity
    │   │   └── res             # Android resources
    │   └── src/iosMain
    │       └── kotlin          # iOS actual platform implementation and Compose UIViewController
    ├── iosApp                 # SwiftUI host app and Xcode project
    ├── gradle/libs.versions.toml
    ├── build.gradle.kts
    └── settings.gradle.kts
```

## How The App Works

1. Android launches `MainActivity` and calls the shared `App()` composable.
2. iOS launches the SwiftUI `ContentView`, which embeds the shared Compose `MainViewController()`.
3. `App()` displays a button.
4. Tapping the button toggles animated content.
5. The shared `Greeting` class calls the platform-specific `getPlatform()` implementation.

## Getting Started

1. Clone the repository.
2. Open the `CurrencyApp` folder in Android Studio.
3. Sync Gradle.
4. Run `composeApp` on Android.
5. Open `CurrencyApp/iosApp/iosApp.xcodeproj` in Xcode to run the iOS app.

## Build Examples

```bash
cd CurrencyApp
./gradlew :composeApp:assembleDebug
./gradlew :composeApp:compileKotlinIosSimulatorArm64
```

## Notes

Despite the repository name, the current code does not yet include cryptocurrency APIs, market data, portfolios, charts, persistence, or business logic. It is best treated as a KMM/Compose Multiplatform learning base for a future crypto or currency app.
