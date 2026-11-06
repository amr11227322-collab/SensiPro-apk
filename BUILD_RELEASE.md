# Building the release

## 1) Create a signing key (once, keep it safe, you cannot recover it)
keytool -genkeypair -v -keystore sensipro-release.jks -alias sensipro \
  -keyalg RSA -keysize 2048 -validity 10000

## 2) Configure
cp keystore.properties.example keystore.properties   # then fill in real values

## 3) Build
./gradlew assembleRelease     # APK  -> app/build/outputs/apk/release/
./gradlew bundleRelease       # AAB  -> app/build/outputs/bundle/release/ (for Google Play)

(In Android Studio: Build > Generate Signed Bundle / APK)

## Before each new release
Increase versionCode (and versionName) in app/build.gradle.kts.
