# NetworkApp

An Angular mobile app built with Capacitor for Web, Android, and iOS.

## Prerequisites

- Node.js 18+
- npm
- Angular CLI: `npm install -g @angular/cli`
- For Android: [Android Studio](https://developer.android.com/studio)
- For iOS: Xcode (macOS only)

## Installation

```bash
npm install
```

## Development Server

```bash
ng serve
```

Open http://localhost:4200 in your browser.

---

## Build for Web

```bash
ng build
```

Output: `dist/network-app/browser/`

To preview the production build:
```bash
npx serve dist/network-app/browser
```

---

## Build for Android

### First-time setup
```bash
# Install Capacitor CLI (if not installed)
npm install @capacitor/cli @capacitor/core @capacitor/android

# Add Android platform (already done)
npx cap add android
```

### Build & Run
```bash
# Build web + sync to Android
npm run cap:android
```

This opens Android Studio. Then:
1. Wait for Gradle sync to complete
2. Click ▶️ Run or `Shift+F10`
3. Select emulator or connected device

### Build APK
In Android Studio:
1. Build → Build Bundle(s) / APK(s) → Build APK(s)
2. APK location: `android/app/build/outputs/apk/debug/app-debug.apk`

### Build Release APK
```bash
cd android
./gradlew assembleRelease
```
Output: `android/app/build/outputs/apk/release/app-release-unsigned.apk`

---

## Build for iOS (macOS only)

### First-time setup
```bash
# Install Capacitor iOS (if not installed)
npm install @capacitor/ios

# Add iOS platform (already done)
npx cap add ios

# Install CocoaPods dependencies
cd ios/App && pod install && cd ../..
```

### Build & Run
```bash
# Build web + sync to iOS
npm run cap:ios
```

This opens Xcode. Then:
1. Select your target device/simulator
2. Click ▶️ Run or `Cmd+R`

### Build for App Store
In Xcode:
1. Product → Archive
2. Distribute App → App Store Connect

---

## Useful Commands

| Command | Description |
|---------|-------------|
| `ng serve` | Start dev server |
| `ng build` | Build for production |
| `npm run cap:sync` | Build web + sync to native |
| `npm run cap:android` | Build + open Android Studio |
| `npm run cap:ios` | Build + open Xcode |
| `npx cap sync` | Sync web build to native projects |
| `npx cap copy` | Copy web assets only (faster) |

---

## Project Structure

```
├── src/                  # Angular source code
├── dist/                 # Web build output
├── android/              # Android native project
├── ios/                  # iOS native project
├── capacitor.config.ts   # Capacitor configuration
└── angular.json          # Angular configuration
```

## Troubleshooting

### Android: Gradle sync failed
```bash
cd android && ./gradlew clean && cd ..
npx cap sync android
```

### iOS: Pod install failed
```bash
cd ios/App && pod install --repo-update && cd ../..
```

### Changes not showing on device
```bash
npm run cap:sync
```
