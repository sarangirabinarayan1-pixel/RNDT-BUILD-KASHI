name: RNDT Cloud Abhishek
on:
  workflow_dispatch:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'
      - name: Build AAB
        run: |
          cd android
          ./gradlew bundleRelease
      - name: Upload AAB
        uses: actions/upload-artifact@v4
        with:
          name: RNDT-Release-AAB
          path: android/app/build/outputs/bundle/release/app-release.aab