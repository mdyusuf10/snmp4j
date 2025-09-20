# SNMP4J-Agent 2.5.0 — Java 8 Support

Date: 2025-09-20

## Summary
SNMP4J-Agent now officially targets Java 8. The build has been updated to compile and run on JDK 8, with Javadoc doclint disabled for compatibility.

## Highlights
- Minimum Java version is now 8.
- Maven build updated to compile with source/target 1.8.
- Ant build updated to compile with source/target 1.8.
- Javadoc doclint disabled to avoid strict JDK 8 checks.

## Breaking Changes
- Minimum supported JDK raised from 1.6 to 1.8.
- Projects running on Java 6/7 must upgrade their runtime and toolchains to Java 8.

## Build/Tooling
- Maven (`pom.xml`):
  - `maven-compiler-plugin` set to:
    ```xml
    <source>1.8</source>
    <target>1.8</target>
    ```
  - `maven-compiler-plugin` version: 3.11.0.
  - `maven-javadoc-plugin` configured to disable doclint:
    ```xml
    <additionalparam>-Xdoclint:none</additionalparam>
    ```

- Ant (`build.xml`):
  - `javac` updated to `source="1.8" target="1.8"`.
  - `javadoc` updated with `additionalparam="-Xdoclint:none"`.

## Compatibility
- Runtime: Requires Java 8+.
- `snmp4j` dependency remains at 2.3.4; compatible with Java 8.
- No public API changes introduced specifically for Java 8 enablement.

## Migration Notes
- Ensure your build toolchain uses JDK 8.
- Update Maven projects to use `<source>1.8</source>` / `<target>1.8</target>` or `<release>8</release>` (if building with JDK 9+ toolchains).
- Validate TLS/JCE provider configurations after upgrading the JDK, as defaults may differ from older versions.

## Known Issues
- None specific to Java 8 at this time. If you encounter doclint or JCE/provider issues, please file an issue with JDK version and repro details.

## Acknowledgements
Thanks to contributors who helped test builds and runtime on Java 8 across Maven and Ant.
