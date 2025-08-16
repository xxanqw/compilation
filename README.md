# Minecraft Mod Compilation Action

A simple GitHub Action to compile your Minecraft mod using Gradle.

## Features

- Easy to use - just add to your workflow
- Configurable Java version (17, 21, 24, etc.)
- Uses latest GitHub Actions (checkout@v4, setup-java@v3)
- Automatic Gradle wrapper execution

## Usage

>[!NOTE]
>You need to checkout your repository before running this action

### Basic Usage (Java 21 - default)

```yaml
name: Build Minecraft Mod

on:
  push:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout
      uses: actions/checkout@v4
      with:
          fetch-depth: 0

    - name: Compile Mod
      uses: xxanqw/compilation@v3
      
    - name: Upload Artifacts
      uses: actions/upload-artifact@v4
      with:
        name: mod-artifacts
        path: ./build/libs
```

### Custom Java Version

```yaml
name: Build Minecraft Mod

on:
  push:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout
      uses: actions/checkout@v4
      with:
          fetch-depth: 0

    - name: Compile Mod with Java 17
      uses: xxanqw/compilation@v3
      with:
        java-version: "17"
      
    - name: Upload Artifacts
      uses: actions/upload-artifact@v4
      with:
        name: mod-artifacts
        path: ./build/libs
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `java-version` | Java version to use (e.g., 17, 21, 24) | No | `21` |

## Requirements

- Your repository must contain a Gradle-based Minecraft mod project
- Must have `gradlew` (Gradle wrapper) in the root directory
- Standard Gradle build configuration

## Credits

Original action created by [Ruochenfu2011](https://github.com/Ruochenfu2011). Updated and modernized by [xxanqw](https://github.com/xxanqw) with support for configurable Java versions and latest GitHub Actions.
