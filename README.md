
App Name – React Native Weather App

Overview
App Name is a cross-platform weather app built with React Native (JavaScript) and a Kotlin native module for Android-specific functionality. It fetches real-time weather and forecast data, supports location-based weather, and features a responsive UI with light/dark themes.

Features

Current weather: temperature, conditions, humidity, wind, feels-like

7-day forecast and hourly forecast

Location-based weather (GPS) + search by city

Theming: light/dark mode with system preference

Offline-friendly caching for last known weather

Kotlin native module on Android for location and/or performance-critical tasks

Error and loading states with graceful fallbacks

Tech Stack

React Native (JavaScript/TypeScript optional)

Kotlin (Android Native Module)

React Navigation

State management: Redux/Zustand/Recoil/Context (pick your actual choice)

Networking: fetch/axios + AbortController

Styling: StyleSheet/Styled Components/Tailwind RN (pick your actual choice)

Architecture

app/

components/ – Presentational UI components

screens/ – Home, Search, Forecast, Settings

hooks/ – Custom hooks (useWeather, useLocation)

store/ – State management logic

services/ – API clients (weather, geocoding), caching

utils/ – Formatters, constants, theme

native/

android/ – Kotlin module(s) (e.g., LocationModule)

index.js / App.js – entry points

Getting Started

Prerequisites

Node.js >= 18

Java 17 (for Android)

Android Studio + Android SDK

Xcode 15+ (for iOS, on macOS)

CocoaPods (for iOS): gem install cocoapods

Installation

Clone and install

git clone https://github.com/your-username/your-repo.git

cd your-repo

npm install or yarn install

Environment variables
Create a .env file (or use react-native-config) with:

WEATHER_API_KEY=your_api_key

WEATHER_API_BASE=https://api.example.com

GEO_API_KEY=your_geo_key (if applicable)

iOS setup (macOS only)

cd ios && pod install && cd ..

npx react-native run-ios
Or open ios/AppName.xcworkspace in Xcode and run.

Android setup

Start an Android emulator or connect a device with USB debugging

npx react-native run-android

Kotlin Native Module (Android)

LocationModule written in Kotlin provides:

getCurrentLocation(): Promise<Location>

watchLocation(callback): Subscription

Located at android/app/src/main/java/com/yourapp/location/LocationModule.kt

Ensure MainApplication.java/Kotlin registers the package

Add permissions in AndroidManifest.xml:

ACCESS_COARSE_LOCATION

ACCESS_FINE_LOCATION

ACCESS_BACKGROUND_LOCATION (if needed)

Request runtime permissions in JS before accessing location

Configuration

Permissions

Android: ACCESS_COARSE_LOCATION, ACCESS_FINE_LOCATION, INTERNET

iOS: NSLocationWhenInUseUsageDescription in Info.plist, plus NSAppTransportSecurity exceptions if needed

API Provider

Replace the weather API base URL and key in services/weather.ts

Implement rate limiting, retries, and caching as desired

Env and Build Variants

.env.development, .env.production supported via react-native-config

Android: build.gradle productFlavors (dev, prod)

iOS: Schemes/Configurations for dev/prod

Scripts

start: npx react-native start

android: npx react-native run-android

ios: npx react-native run-ios

lint: eslint . --ext .js,.jsx,.ts,.tsx

typecheck: tsc --noEmit

test: jest

clean: watchman watch-del-all && rm -rf node_modules && npm i

Usage

Open the app

Grant location permission to auto-detect your city

Search by city name from the Search screen

Toggle theme in Settings if not following system

Screenshots

Add screenshots/GIFs in a docs/ folder and reference them here:

docs/home-light.png

docs/home-dark.png

docs/forecast.png

Development Notes

State: describe your chosen library and store shape briefly

Error handling: show inline errors with retry; network timeouts ~8–12s

Accessibility: labeled touch targets, sufficient contrast, dynamic type

Performance: FlatList for forecasts, memoized components, image caching

Offline: display last successful fetch; show “updated x min ago”

Testing

Unit tests: Jest + React Native Testing Library

E2E: Detox (Android/iOS)

Kotlin module tests: JUnit/robolectric for Android-side logic

CI/CD

Suggested: GitHub Actions with matrix for lint, test, Android build, iOS build

Android signing via Gradle keystore; iOS via Fastlane match or Xcode Cloud

Increment versionCode/version and changelog per release

Troubleshooting

Metro stuck: kill node processes, run npm run clean, reset cache: npx react-native start --reset-cache

Android build fails with Kotlin/Gradle mismatch: align Kotlin, Gradle, AGP versions in build.gradle

iOS Pods errors: pod repo update and pod install; clear DerivedData

Location not updating on Android: verify permissions and that LocationModule is registered

Roadmap

Widgets and notifications for severe weather alerts

Multi-language i18n

Air quality index and radar map

Unit preferences (C/°F, km/h/mph)

Wear OS / Apple Watch companion

License

MIT (or your preferred license). See LICENSE file.

Contributing

Fork, create a feature branch, commit with conventional commits, open PR.

Run lint, tests, and typecheck before submitting.

Acknowledgements

Weather data by Your Provider

Icons by Your Icon Set

Thanks to the React Native and Kotlin communities
