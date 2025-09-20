SNMP4J — Java 8 Support

Summary We are pleased to announce official Java 8 support for SNMP4J. This release has been compiled and tested with JDK 8, and SNMP4J can now be used seamlessly within Java 8 applications and build pipelines.

Highlights

Official Java 8 support: Built and validated with JDK 8.
Compatibility maintained: No public API breaking changes introduced for enabling Java 8 support.
Toolchain updates: Build and tests run successfully on JDK 8 across common build tools.
Compatibility

Runtime: SNMP4J now fully supports running on Java 8.
Existing Users: No code changes are required for typical use cases when running on Java 8.
Older JDKs: If you still target older JDKs (e.g., Java 7/6), please confirm with your build profile. This release does not intentionally drop older runtime compatibility, but your project’s compiler settings determine what bytecode is produced for your artifacts.
Build/Tooling

Maven users can target Java 8 with the following in your project’s pom:
Either using maven-compiler-plugin: org.apache.maven.plugins maven-compiler-plugin 3.11.0 1.8 1.8 UTF-8
Or using release flag (requires JDK 9+ toolchains, produces Java 8 bytecode): 8
Gradle users can set: java { sourceCompatibility = JavaVersion.VERSION_1_8 targetCompatibility = JavaVersion.VERSION_1_8 }
API Surface

No new public API is required specifically for Java 8 support.
No deprecations introduced exclusively due to Java 8 support.
If you leverage Java 8 features in your application (e.g., lambdas, streams), you can now do so while using SNMP4J on the same runtime without workarounds.
Migration Notes

If you previously ran SNMP4J on Java 7/6 and are moving your application to Java 8:
Rebuild your application with Java 8 compiler settings (see Build/Tooling).
Validate any TLS/SSL or security provider configurations on Java 8, as underlying JDK security defaults may differ from older JDKs.
Run your existing integration tests; no SNMP4J-specific code changes are expected.
Known Issues

None specific to Java 8 support at this time.
If you encounter issues related to JCE providers or TLS ciphers on Java 8, please open an issue with details on your JDK version, provider configuration, and a minimal reproduction.
Acknowledgements

Thanks to the contributors who tested and validated SNMP4J with JDK 8 across different environments and build setups.
Call to Action

Try the release on Java 8 and report any regressions or environment-specific issues.
If you need us to explicitly document minimum JDK requirements (e.g., raising the minimum to 1.8), let us know and we will update these notes accordingly.