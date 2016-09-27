---
title: >-
  ModbusMaster v1.0.0 released
date: 2016-09-11 21:00:00
categories:
  - Arduino
subcategories:
  - Modbus
tags:
  - arduino
  - c++
  - library
  - modbus
  - modbus master
  - plc
  - rs232
  - rs485
  - rtu
  - serial
---

#### Overview

`ModbusMaster` is an Arduino library for communicating with Modbus slaves over RS232/485 (via RTU protocol). Version 1.0.0 was released on 11 Sep 2016 and includes a number of changes.

<!-- more -->

#### Features
The following Modbus functions are available:

Discrete Coils/Flags

  - 0x01 - Read Coils
  - 0x02 - Read Discrete Inputs
  - 0x05 - Write Single Coil
  - 0x0F - Write Multiple Coils

Registers

  - 0x03 - Read Holding Registers
  - 0x04 - Read Input Registers
  - 0x06 - Write Single Register
  - 0x10 - Write Multiple Registers
  - 0x16 - Mask Write Register
  - 0x17 - Read Write Multiple Registers

Both full-duplex and half-duplex RS232/485 transceivers are supported. Callback functions are provided to toggle Data Enable (DE) and Receiver Enable (/RE) pins.

#### Change log

[Full Changelog](https://github.com/4-20ma/ModbusMaster/compare/v0.11.0...v1.0.0)

**Implemented enhancements:**

- Add continuous integration testing with travis [\#55](https://github.com/4-20ma/ModbusMaster/issues/55)
- Add Code of Conduct [\#54](https://github.com/4-20ma/ModbusMaster/issues/54)
- Create PULL\_REQUEST\_TEMPLATE [\#49](https://github.com/4-20ma/ModbusMaster/issues/49)
- Create ISSUE\_TEMPLATE [\#48](https://github.com/4-20ma/ModbusMaster/issues/48)
- Change license to Apache 2.0 [\#45](https://github.com/4-20ma/ModbusMaster/issues/45)
- Set \_\_MODBUSMASTER\_DEBUG\_\_ to 0 by default [\#35](https://github.com/4-20ma/ModbusMaster/issues/35)
- Pass Stream object instead of integer reference [\#17](https://github.com/4-20ma/ModbusMaster/issues/17)
- Add LICENSE, convert project to Apache 2.0 [\#67](https://github.com/4-20ma/ModbusMaster/pull/67) ([4-20ma](https://github.com/4-20ma))
- Add example sketch for half-duplex RS485 [\#66](https://github.com/4-20ma/ModbusMaster/pull/66) ([kintel](https://github.com/kintel))
- Add continuous integration testing with Travis CI [\#63](https://github.com/4-20ma/ModbusMaster/pull/63) ([4-20ma](https://github.com/4-20ma))
- Add initial .travis.yml configuration [\#62](https://github.com/4-20ma/ModbusMaster/pull/62) ([4-20ma](https://github.com/4-20ma))
- Add CODE\_OF\_CONDUCT [\#56](https://github.com/4-20ma/ModbusMaster/pull/56) ([4-20ma](https://github.com/4-20ma))
- Add initial PULL\_REQUEST\_TEMPLATE [\#53](https://github.com/4-20ma/ModbusMaster/pull/53) ([4-20ma](https://github.com/4-20ma))
- Add initial ISSUE\_TEMPLATE [\#50](https://github.com/4-20ma/ModbusMaster/pull/50) ([4-20ma](https://github.com/4-20ma))
- Add preTransmission\(\), postTransmission\(\) for half-duplex [\#44](https://github.com/4-20ma/ModbusMaster/pull/44) ([kintel](https://github.com/kintel))
- Disable \_\_MODBUSMASTER\_DEBUG\_\_ mode by default [\#43](https://github.com/4-20ma/ModbusMaster/pull/43) ([kintel](https://github.com/kintel))
- Add STYLE coding style guide [\#29](https://github.com/4-20ma/ModbusMaster/pull/29) ([4-20ma](https://github.com/4-20ma))

**Closed issues:**

- Fix documentation references in ModbusMaster.h, .cpp [\#69](https://github.com/4-20ma/ModbusMaster/issues/69)
- Clean up template wording [\#64](https://github.com/4-20ma/ModbusMaster/issues/64)
- Add Label section to CONTRIBUTING [\#60](https://github.com/4-20ma/ModbusMaster/issues/60)
- Update README contact information [\#58](https://github.com/4-20ma/ModbusMaster/issues/58)

**Merged pull requests:**

- Clean up ISSUE/PULL\_REQUEST templates [\#65](https://github.com/4-20ma/ModbusMaster/pull/65) ([4-20ma](https://github.com/4-20ma))
- Add label guidance to CONTRIBUTING [\#61](https://github.com/4-20ma/ModbusMaster/pull/61) ([4-20ma](https://github.com/4-20ma))
- Update README contact information [\#59](https://github.com/4-20ma/ModbusMaster/pull/59) ([4-20ma](https://github.com/4-20ma))
- Add email address to CODE\_OF\_CONDUCT [\#57](https://github.com/4-20ma/ModbusMaster/pull/57) ([4-20ma](https://github.com/4-20ma))
- Clarify instructions in ISSUE\_TEMPLATE [\#52](https://github.com/4-20ma/ModbusMaster/pull/52) ([4-20ma](https://github.com/4-20ma))
- Add ISSUE\_TEMPLATE title reqs, separator lines [\#51](https://github.com/4-20ma/ModbusMaster/pull/51) ([4-20ma](https://github.com/4-20ma))

#### License

```
Copyright:: 2009-2016 Doc Walker

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

#### Resources

<span class="fa fa-github"> [4-20ma][user] / [ModbusMaster][source]
<span class="fa fa-info-circle"> Source Code [Documentation][docs]
<span class="fa fa-info-circle"> Modicon Modbus Protocol Reference Guide [PI-MBUS-300][modbus-protocol]

[user]:             https://github.com/4-20ma
[source]:           https://github.com/4-20ma/ModbusMaster
[docs]:             http://4-20ma.io/ModbusMaster/
[modbus-protocol]:  http://modbus.org/docs/PI_MBUS_300.pdf
