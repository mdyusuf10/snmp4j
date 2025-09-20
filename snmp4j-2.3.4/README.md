# SNMP4J

SNMP4J is a free and open source Java SNMP (Simple Network Management Protocol) framework supporting SNMPv1, v2c, and v3.
It provides both client (manager) and agent functionality, enabling developers to integrate SNMP communication into Java applications.

## ✨ Features
- Full support for SNMPv1, v2c, and v3
- Implements GET, GETNEXT, GETBULK, SET, INFORM, and TRAP operations
- Supports IPv4, IPv6, and TLS/DTLS transport mappings
- Extensible message processing and security models
- Thread-safe API for concurrent SNMP operations
- Used widely in network monitoring, device management, and performance analytics

## 📦 Installation
### Maven
Add the dependency to your `pom.xml`:
```xml
<dependency>
  <groupId>org.snmp4j</groupId>
  <artifactId>snmp4j</artifactId>
  <version>2.3.4</version>
</dependency>
```

### Gradle
```gradle
implementation 'org.snmp4j:snmp4j:2.3.4'
```

Or build from source (see below).

## 🔧 Build from Source
Clone the repository:
```bash
git clone https://github.com/GEBIT/snmp4j.git
cd snmp4j
```

Build with Maven:
```bash
mvn clean install
```

Run tests:
```bash
mvn test
```

## 🚀 Quick Example
### Manager Example
```java
TransportMapping<UdpAddress> transport = new DefaultUdpTransportMapping();
Snmp snmp = new Snmp(transport);
transport.listen();

CommunityTarget target = new CommunityTarget();
target.setCommunity(new OctetString("public"));
target.setAddress(GenericAddress.parse("udp:127.0.0.1/161"));
target.setRetries(2);
target.setTimeout(1500);
target.setVersion(SnmpConstants.version2c);

PDU pdu = new PDU();
pdu.add(new VariableBinding(new OID("1.3.6.1.2.1.1.1.0")));
pdu.setType(PDU.GET);

ResponseEvent response = snmp.get(pdu, target);
System.out.println("Response: " + response.getResponse());
```

## 🤝 Contributing
Contributions are welcome!
- Fork the repository
- Create a new branch (`git checkout -b fix-issue-name`)
- Make your changes
- Run tests (`mvn test`)
- Open a Pull Request

Please check open issues for tasks suitable for new contributors.

## 📜 License
SNMP4J is licensed under the Apache License 2.0.
See LICENSE for details.

## 📚 Resources
- Official Website
- JavaDocs
- SNMP RFCs
