
name: Compilar Soluciones 70

on:
  workflow_dispatch:
  push:
    paths:
      - 'Soluciones70_Android_Proyecto.zip'
      - '.github/workflows/build.yml'

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - uses: gradle/actions/setup-gradle@v4
        with:
          gradle-version: '8.9'

      - name: Preparar proyecto
        run: |
          unzip Soluciones70_Android_Proyecto.zip
          ls -la

      - name: Compilar APK
        run: |
          find . -name gradlew -type f
          cd soluciones70_android
          gradle assembleDebug
# soluciones70-android
Aplicación de gestión Soluciones 70
