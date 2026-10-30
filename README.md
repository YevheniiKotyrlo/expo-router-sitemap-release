# expo-router `/_sitemap` crashes in a release build

A blank Expo app (`npx create-expo-app@latest --template blank`) with Expo Router installed as the docs describe, and one screen that links to `/_sitemap`.

## Steps

1. `npm install`
2. `npx expo run:android --variant release` (or `npx expo prebuild -p android` and `cd android && ./gradlew assembleRelease`, then install `app-release.apk`)
3. Open the app and tap **Open sitemap**.

**Expected:** the sitemap screen opens, as it does in a development build.

**Actual:** the app closes. Logcat shows:

```
E/ReactNativeJS: { [TypeError: Cannot read property 'origin' of undefined]
E/ReactNativeJS:   componentStack: '\n    at SystemInfo (address at index.android.bundle:1:936467)\n ...
E/AndroidRuntime: FATAL EXCEPTION: mqt_v_native
E/AndroidRuntime: com.facebook.react.common.JavascriptException: TypeError: Cannot read property 'origin' of undefined
```
