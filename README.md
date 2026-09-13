# EmonHisab1
name: Build APK

on:
  push:
    branches: [ "main", "master" ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4

    - name: Unzip project
      run: |
        unzip -o EmonHisab.zip || unzip -o *.zip
        if [ -d "EmonHisab" ]; then cp -rn EmonHisab/* . || true; fi

    - name: Set up JDK 17
      uses: actions/setup-java@v4
      with:
        java-version: '17'
        distribution: 'temurin'

    - name: Make gradlew executable
      run: chmod +x gradlew

    - name: Build Debug APK
      run: ./gradlew assembleDebug

    - name: Upload APK
      uses: actions/upload-artifact@v4
      with:
        name: EmonHisab-APK
        path: '**/build/outputs/apk/debug/*.apk'
