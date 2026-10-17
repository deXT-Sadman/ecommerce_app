# Evira

Evira is a Flutter e-commerce application built for browsing products, managing a cart, signing in, checking out, and tracking orders. The app uses a layered architecture with feature-based folders, Provider state management, GoRouter navigation, and Dio-based API access.

## Features

- Product catalog with search and category filters
- Product details with pricing, metadata, and image previews
- Shopping cart with quantity updates and sync-aware state
- Authentication flow for user sign-in and profile access
- Checkout and order placement flow
- Order history and success confirmation screens
- Payment page integration via webview-based payment flow
- Local persistence with SharedPreferences for auth and cart state

## Tech Stack

- Flutter
- Dart
- Provider
- GoRouter
- Dio
- SharedPreferences
- cached_network_image
- webview_flutter
- json-server (local mock backend)

## Architecture

The project follows a feature-first structure:

- `lib/features/` contains feature domains such as auth, cart, product, order, and payment
- `lib/core/` contains shared network, router, storage, theme, and constants
- `lib/app.dart` wires up the app-level providers and router
- `mock_server/` provides a local JSON mock API used for order operations

Additional design notes and implementation guides are included in the docs folder:

- [doc/flutter_provider_pattern_plan.md](doc/flutter_provider_pattern_plan.md)
- [doc/immutable_models_guide.md](doc/immutable_models_guide.md)

## Project Structure

```text
lib/
  app.dart
  main.dart
  core/
    constants/
    network/
    router/
    storage/
    theme/
    widgets/
  features/
    auth/
    cart/
    order/
    payment/
    product/
mock_server/
  db.json
  package.json
  README.md
```

## Prerequisites

Before running the app, make sure you have:

- Flutter SDK 3.12 or newer
- Dart SDK included with Flutter
- Node.js and npm (for the local mock API)
- An Android emulator, iOS simulator, or a connected device

## Getting Started

### 1. Install Flutter dependencies

```bash
flutter pub get
```

### 2. Start the mock server

```bash
cd mock_server
npm install
npm start
```

The mock server runs on:

- `http://localhost:3001`
- `http://10.0.2.2:3001` for Android emulators

### 3. Run the app

```bash
flutter run
```

If you are using Android Studio or VS Code with Flutter support, you can also launch the app from the IDE. The app is configured to access the local order backend through the Android emulator host and localhost for desktop/simulator environments.

## Default App Flow

The app starts at the product catalog, where users can:

- browse and search products
- open product detail screens
- add items to the cart
- sign in from the profile area
- proceed to checkout
- complete payment and view order confirmation

## Notes

- Product listings use the remote DummyJSON API by default.
- Order, checkout, and related transactional flows rely on the local mock server under `mock_server/`.
- Persistent app state such as auth and cart data is stored locally using SharedPreferences.

## Useful Commands

```bash
flutter analyze
flutter test
flutter run -d chrome
```

## License

This project is currently unlicensed and intended for local development and learning purposes.

