# React Native TypeScript Starter

A production-ready React Native starter template with TypeScript, configured for iOS and Android development.

## Stack

- **React Native 0.83.1** - Latest stable version
- **TypeScript** - Full type safety throughout
- **React Native CLI** - No Expo, full control over native code
- **VS Code** - Configured with debugging support
- **iOS & Android** - Native support for both platforms

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
git clone <your-repo-url>
cd react-native-starter
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

**Note:** This project includes custom fixes for Ruby 4.0+ compatibility:
- `Gemfile` includes `nkf` gem for Ruby 4.0 stdlib compatibility
- `ios/Podfile` uses direct require for `react_native_pods.rb`

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
2. Install the **React Native Tools** extension (msjsdiag.vscode-react-native)
3. Press **F5** and select:
   - **Debug iOS** - Launch iOS simulator with debugging
   - **Debug Android** - Launch Android emulator with debugging
   - **Attach to packager** - Attach to running Metro bundler

Set breakpoints in TypeScript files and debug with full variable inspection.

### Hot Reload

When Metro is running, changes to your code will automatically refresh:
- Save any `.tsx` or `.ts` file
- The app updates instantly in the simulator/emulator

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

## Troubleshooting

### iOS Build Issues

**"database is locked" error:**
```bash
killall -9 xcodebuild
rm -rf ~/Library/Developer/Xcode/DerivedData/ReactNativeStarter-*
npm run ios
```

**CocoaPods issues:**
```bash
cd ios
rm -rf Pods Podfile.lock
bundle exec pod install --repo-update
cd ..
```

### Android Build Issues

**Gradle build fails:**
```bash
cd android
./gradlew clean
cd ..
npm run android
```

**Multiple builds running:**
```bash
./gradlew --stop
```

### General Issues

**Metro bundler issues:**
```bash
npm start -- --reset-cache
```

**Clean everything:**
```bash
rm -rf node_modules
npm install
cd ios && rm -rf Pods Podfile.lock && bundle exec pod install && cd ..
cd android && ./gradlew clean && cd ..
```

## Key Configuration Files

### Modified from Default Template

1. **`Gemfile`** - Added `nkf` gem for Ruby 4.0+ compatibility
2. **`ios/Podfile`** - Uses direct require instead of node resolution
3. **`.vscode/`** - Added debugging configurations
4. **`.gitignore`** - Excludes `.bundle/`, `Gemfile.lock`, `install-pods.sh`

## Next Steps

### Recommended Additions

- **Navigation**: [React Navigation](https://reactnavigation.org/)
- **State Management**: [Zustand](https://github.com/pmndrs/zustand) or [Redux Toolkit](https://redux-toolkit.js.org/)
- **UI Library**: [React Native Paper](https://reactnativepaper.com/) or [NativeBase](https://nativebase.io/)
- **Forms**: [React Hook Form](https://react-hook-form.com/)
- **API Client**: [Axios](https://axios-http.com/) or [TanStack Query](https://tanstack.com/query)
- **Testing**: [React Native Testing Library](https://callstack.github.io/react-native-testing-library/)

### Path Aliases

Consider adding path aliases to `tsconfig.json`:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@components/*": ["src/components/*"],
      "@screens/*": ["src/screens/*"],
      "@utils/*": ["src/utils/*"]
    }
  }
}
```

## Resources

- [React Native Documentation](https://reactnative.dev/docs/getting-started)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [React Native Debugging Guide](https://reactnative.dev/docs/debugging)
- [React Native Performance](https://reactnative.dev/docs/performance)

## License

MIT
