# SNMP4J-Agent

SNMP4J-Agent provides a modular framework for building SNMP agents (v1/v2c/v3) on top of the SNMP4J library. It implements core MIB modules, request processing, VACM/USM security, and utilities for building managed objects.

- Homepage: https://www.snmp4j.org
- Module: `snmp4j-agent`
- License: Apache-2.0

## What's New (2.5.0)
- Official Java 8 support (minimum JDK is now 1.8).
- Maven and Ant builds updated to compile with `source=1.8` and `target=1.8`.
- Javadoc doclint disabled for JDK 8 for compatibility.

See `Release_Notes.md` and `CHANGES.txt` for details.

## Requirements
- Java 8 or newer (JRE/JDK).
- SNMP4J 2.4.0 or newer.

## Build

### Maven
This module is a Maven project. Typical commands:

```bash
# Build jar
mvn -DskipTests package

# Run tests
mvn test

# Install to local repo
mvn install
```

Compiler configuration is set in `pom.xml` to target Java 8 using `maven-compiler-plugin`.

### Ant
An Ant build is also provided for legacy workflows via `build.xml`.

Common targets:
- `ant compile` – compile classes
- `ant package` – build jar and javadocs
- `ant rebuild` – clean and rebuild

`javac` is configured with `source="1.8"` and `target="1.8"`. Javadoc runs with `-Xdoclint:none`.

## Using SNMP4J-Agent
Add dependencies to your project and configure a basic agent using `AgentConfigManager` or extend `BaseAgent`.

Example (simplified):

```java
// Create and configure an agent (skeleton example)
TransportMapping<?> transport = new DefaultUdpTransportMapping(new UdpAddress("0.0.0.0/161"));
MessageDispatcher dispatcher = new MessageDispatcherImpl();
dispatcher.addMessageProcessingModel(new MPv1());
dispatcher.addMessageProcessingModel(new MPv2c());
dispatcher.addMessageProcessingModel(new MPv3());

Snmp snmp = new Snmp(dispatcher, transport);
// Configure USM/VACM, MIBs, and start listening...
transport.listen();
```

For comprehensive samples, explore the `src` tree and the sample agents, and consult SNMP4J documentation.

## Documentation
- Release Notes: `Release_Notes.md`
- Change Log: `CHANGES.txt`
- JavaDoc: generate with `mvn javadoc:javadoc` or `ant javadoc`

## Support & Issues
- Report issues with Java version, provider configuration, and a minimal reproduction when possible.
- Community resources and documentation are available at the SNMP4J website.
