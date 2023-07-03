# Setup Gradle

💿 A simple composite GitHub Action to setup Gradle Build Tool

## Usage

You can use below example workflow in your workflow.

```yml
name: Java CI with Gradle
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Setup Gradle
        uses: TozyF/setup-gradle-action@v1

      - name: Execute Gradle build
        run: ./gradlew build
```

## Inputs

### JDK options

| Input              | Description                                                                                                                                               | Default |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `jdk-version`      | The Java version use to invoke Gradle executable. Takes a whole or [semver](https://github.com/actions/setup-java#supported-version-syntax) Java version. | `17`    |
| `jdk-distribution` | The Java [distribution](https://github.com/actions/setup-java#supported-distributions)                                                                    | `zulu`  |
| `check-latest-jdk` | Check for the latest available Java version that satisfies the version spec                                                                               | `false` |

### Gradle options

| Input                            | Description                                                                                                                                              | Default                      |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| `gradle-version`                 | The Gradle version to use                                                                                                                                | `wrapper`                    |
| `gradle-executable`              | Path to the Gradle executable                                                                                                                            |                              |
| `cache-disabled`                 | Disable Gradle cache                                                                                                                                     | `false`                      |
| `cache-read-only`                | Existing entries will be read from the cache but no entries will be written                                                                              | [action.yml](action.yml#L41) |
| `cache-write-only`               | Entries will not be restored from the cache but will be saved at the end of the Job                                                                      | `false`                      |
| `gradle-home-cache-includes`     | Paths within Gradle User Home to cache                                                                                                                   | `caches`<br>`notifications`  |
| `gradle-home-cache-excludes`     | Paths within Gradle User Home to exclude from cache                                                                                                      |                              |
| `generate-job-summary`           | Generates a summary of the Gradle build for the job                                                                                                      | `true`                       |
| `gradle-home-cache-strict-match` | Not attempt to restore the Gradle User Home entries from other Jobs                                                                                      | `false`                      |
| `gradle-home-cache-cleanup`      | attempt to remove any stale/unused entries from the Gradle User Home prior to saving to the GitHub Actions cache                                         | `true`                       |
| `gradle-wrapper-validation`      | Should the action validates the checksums of Gradle Wrapper JAR files present in the source tree and fails if unknown Gradle Wrapper JAR files are found | `true`                       |

_Details about some options can be found [here](https://github.com/marketplace/actions/gradle-build-action)._

## License

Setup Gradle is distributed under the `MIT` license. See [LICENSE](LICENSE) for details.

### Third party licenses

- `setup-java`: [MIT](https://github.com/actions/setup-java/blob/main/LICENSE)
- `gradle-build-action`: [MIT](https://github.com/gradle/gradle-build-action/blob/main/LICENSE)
- `gradle-wrapper-validation`: [MIT](https://github.com/gradle/wrapper-validation-action/blob/main/LICENSE)

## Credits

GitHub actions that the project is using:

- [setup-java](https://github.com/marketplace/actions/setup-java-jdk)
- [gradle-build-action](https://github.com/marketplace/actions/gradle-build-action)
- [gradle-wrapper-validation](https://github.com/marketplace/actions/gradle-wrapper-validation)
