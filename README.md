# React Native TypeScript Starter

React Native starter template with TypeScript, configured for iOS and Android development + VS Code Debugging

## Stack

- **React Native**
- **TypeScript**
- **iOS & Android**

## Prerequisites

### macOS (for iOS development)

- **Node.js 22+** via nvm
- **Xcode 16.2+** with iOS 18.3+ simulator
- **Android Studio** with Android SDK
- **Java 17** (not Java 8)
- **CocoaPods** for iOS dependencies
- **Watchman** for file watching

### Environment Variables

Ensure these are in your `~/.bash_profile` or `~/.zshrc`:

```bash
# Android SDK
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools

# Java 17 for React Native
export JAVA_HOME=/usr/local/opt/openjdk@17
export PATH=$JAVA_HOME/bin:$PATH
```

## Setup Instructions

### 1. Clone and Install

```bash
git clone https://github.com/jacklenzotti/react-native-starter
npm install
```

### 2. iOS Setup

Install Ruby dependencies and CocoaPods:

```bash
# Install Ruby gems (includes CocoaPods)
bundle install

# Install iOS native dependencies
cd ios
export PATH=/usr/local/opt/ruby/bin:$PATH
export LANG=en_US.UTF-8
export PATH="$HOME/.nvm/versions/node/v22.20.0/bin:$PATH"
bundle exec pod install
cd ..
```

### 3. Android Setup

No additional setup needed - just ensure Android Studio and SDK are installed.

## Running the App

### Start Metro Bundler

```bash
npm start
```

### Run on Android

In a new terminal:

```bash
npm run android
```

The Android emulator will launch automatically.

### Run on iOS

In a new terminal:

```bash
npm run ios
```

The iOS simulator will launch automatically.

**Note:** First build takes 5-10 minutes. Subsequent builds are much faster (30-60s).

## Development

### VS Code Debugging

This project is configured for VS Code debugging:

1. Open project in VS Code: `code .`
2. Install the **React Native Tools** extension
3. Press **F5** and select:
   - **Debug iOS** - Launch iOS simulator with debugging
   - **Debug Android** - Launch Android emulator with debugging
   - **Attach to packager** - Attach to running Metro bundler

Set breakpoints in TypeScript files and debug with full variable inspection.

### Hot Reload

When Metro is running, changes to your code will automatically refresh

For manual refresh:
- **iOS**: Press `R` in the simulator
- **Android**: Press `R` twice or `Ctrl+M` (Windows/Linux) or `Cmd+M` (macOS) → Reload

## Project Structure

```
react-native-starter/
├── .vscode/              # VS Code debug configuration
│   ├── launch.json       # Debug configurations
│   └── settings.json     # Editor settings
├── android/              # Android native code
├── ios/                  # iOS native code
├── __tests__/            # Jest tests
├── App.tsx               # Root component
├── index.js              # Entry point
├── package.json          # npm dependencies
├── tsconfig.json         # TypeScript configuration
├── Gemfile               # Ruby dependencies (CocoaPods)
└── babel.config.js       # Babel configuration
```

## Resources

- [React Native Documentation](https://reactnative.dev/docs/getting-started)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [React Native Debugging Guide](https://reactnative.dev/docs/debugging)
- [React Native Performance](https://reactnative.dev/docs/performance)

## License

MIT
