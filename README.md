# UTBotJava-action

An action for unit tests generation and SARIF report creation with the [UTBotJava](https://github.com/UnitTestBot/UTBotJava) engine.

The action imports the SARIF output into GitHub. The SARIF output displays errors in the Security Code Scanning Alerts section.

## Content

- [Usage](#usage)
- [Inputs](#inputs)

## Usage

1. Apply the [UTBot gradle plugin](https://plugins.gradle.org/plugin/org.utbot.gradle.plugin) to your project.
2. Create the workflow with UTBotJava-action. Simple workflow example:

```YAML
name: "Run UTBotJava-action"

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Setup Java
      uses: actions/setup-java@v2
      with:
        distribution: adopt
        java-version: 8

    - name: Setup Gradle
      uses: gradle/gradle-build-action@v2
      with:
        gradle-version: 6.8

    - name: Run UTBotJava-action
      uses: UnitTestBot/UTBotJava-action@main
```
3. Look at the Security Code Scanning Alerts to see the detected errors.

## Inputs

| Name | Description | Default value |
| --- | --- | --- |
| `github_token` | Specify `secrets.GITHUB_TOKEN` here if you want to push generated tests to your __private__ repository. | - |
| `pushTests` | Push generated tests to the repository or not. | 'true' |
